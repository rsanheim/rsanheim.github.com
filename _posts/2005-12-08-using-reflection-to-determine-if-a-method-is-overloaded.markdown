--- 
wordpress_id: 135
layout: post
title: Using reflection to determine method overloading
wordpress_url: http://www.robsanheim.com/?p=135
---
A <a href="http://article.gmane.org/gmane.comp.java.dwr.user/619">thread</a> on the <a href="http://getahead.ltd.uk/dwr/">DWR</a> mailing list about properly detected overloaded methods with covariant types in JDK5 got me curious.  So I put together some quick code to determine if one method overloads another.  It works for covariant types, but I didn't add support for generics.  I'm not sure how much more work that would be.  

Full source code follows.  Feel free to use it if you like it, just leave the attribution.  I'm sure there could be more testing and some optimization done, also.  I would also be very curious to know if anyone else has had to do something similiar.<!--more-->

Here's the <strong>main util class</strong> that does the work:
[java]package com.robsanheim.sandbox.reflection.overloading;

import java.lang.reflect.Method;
import java.util.Arrays;

/**
 * @author Rob Sanheim
 * 
 * A utility to check if one method is overloading another. Note that this
 * utility does not take into account generics at all, but it should work
 * correctly for covariant return types.
 * @link <a *       href="http://java.sun.com/docs/books/jls/third_edition/html/classes.html#227768">the
 *       JLS</a> for information on overloading
 * 
 * TODO change to allow parameters to isOverloaded be ordered any way, and make this 
 * 		class figure out which is the "higher level" method
 * 
 * TODO change to support generics, particularily the nasty case where an
 * 		overloaded or overridden method uses generics and the base method does not -
 * 		see <a * 		href="http://java.sun.com/docs/books/jls/third_edition/html/classes.html#8.4.8.3">JLS
 * 		again</a>
 */
public class OverloadUtil {
	/**
	 * Check two methods reflectively to see if one is overloading the other
	 * Note that the parameter ordering is important if one method is higher in
	 * the class hiearchy then the other. If this is the case, make sure the
	 * method higher up in the chain is the first parameter. Otherwise, the
	 * ordering does not matter.
	 * 
	 * @param higher
	 *            method
	 * @param lower
	 *            method
	 * @return
	 */
	public static boolean isOverloaded(Method higher, Method lower) {
		if (namesAreEqual(higher, lower) && returnTypesAreEqualOrCovariant(higher, lower)
				&& isNotInterfaceImplementation(higher, lower) && isNotOverridden(higher, lower)) {
			return true;

		} else {
			return false;
		}
	}

	private static boolean isNotOverridden(Method higher, Method lower) {
		if (isOverridden(higher, lower)) {
			return false;
		} else {
			return true;
		}
	}

	/**
	 * @param higher
	 * @param lower
	 * @return true if lower overrides higher
	 */
	private static boolean isOverridden(Method higher, Method lower) {
		return declaringClassIsAssignableFrom(higher, lower) && declaringClassIsNotAnInterface(higher)
				&& parametersAreEqual(higher, lower);
	}

	/**
	 * @param first
	 * @param second
	 * @return true if the first method's declaring class is assignable from the
	 *         second
	 */
	private static boolean declaringClassIsAssignableFrom(Method first, Method second) {
		return first.getDeclaringClass().isAssignableFrom(second.getDeclaringClass());

	}

	/**
	 * We have to make sure we don't mistake standard interface implementation
	 * (where first method is on an interface and the params are equal) for
	 * overloading.
	 * 
	 * @param higher
	 * @param lower
	 * @return
	 */
	private static boolean isNotInterfaceImplementation(Method higher, Method lower) {
		return !(declaringClassIsAnInterface(higher) && parametersAreEqual(higher, lower));
	}

	/**
	 * check deep equality on parameters of two methods
	 * 
	 * @param first
	 * @param second
	 * @return
	 */
	private static boolean parametersAreEqual(Method first, Method second) {
		return Arrays.deepEquals(first.getParameterTypes(), second.getParameterTypes());
	}

	/**
	 * @param higher
	 * @param lower
	 * @return true if return types are equal or covariants
	 */
	private static boolean returnTypesAreEqualOrCovariant(Method higher, Method lower) {
		return (declaringClassIsAssignableFrom(higher, lower) || higher.getReturnType().equals(lower.getReturnType()));
	}

	/**
	 * @param first
	 * @param second
	 * @return true if the names of the two methods are equal
	 */
	private static boolean namesAreEqual(Method first, Method second) {
		return first.getName().equals(second.getName());
	}

	private static boolean declaringClassIsAnInterface(Method method) {
		return method.getDeclaringClass().isInterface();
	}

	private static boolean declaringClassIsNotAnInterface(Method method) {
		return !declaringClassIsAnInterface(method);
	}

}
[/java]

<strong>Test case:</strong>
[java]package com.robsanheim.sandbox.reflection.overloading;

import java.lang.reflect.Method;

import junit.framework.TestCase;

/**
 * @author Rob Sanheim
 * 
 * Test OverloadUtil
 * Unless otherwise noted, we cannot assume that isOverloaded(x, y) == isOverloaded(y, x)
 */
public class OverloadUtilTest extends TestCase {
	private static final String METHOD = "method";
	private static final String ANOTHER_METHOD = "anotherMethod";
	private static final Class[] NO_PARAMETERS = null;
	// fixtures
	private Method returnsStringNoParameters = getMethod(ConcreteClass.class, METHOD, NO_PARAMETERS);
	private Method returnsStringOneParameter = getMethod(ConcreteClass.class, METHOD, String.class);
	private Method returnsObjectNoParametersDifferentName = getMethod(ConcreteClass.class, ANOTHER_METHOD,
			NO_PARAMETERS);
	private Method returnsStringNoParametersOnSubClass = getMethod(SubClass.class, METHOD, NO_PARAMETERS);
	private Method returnsObjectThreeParametersOnSubClass = getMethod(SubClass.class, METHOD, String.class,
			String.class, String.class);
	private Method returnsObjectNoParametersOnInterfaceType = getMethod(Interface.class, METHOD, NO_PARAMETERS);

	/**
	 * This type of test should be reversible
	 * 
	 * @throws Exception
	 */
	public void testTwoSimpleOverloadedMethodsOnSameClass() throws Exception {
		assertTrue(OverloadUtil.isOverloaded(returnsStringNoParameters, returnsStringOneParameter));
		assertTrue(OverloadUtil.isOverloaded(returnsStringOneParameter, returnsStringNoParameters));
	}

	public void testMoreSpecificMethodOnConcreteClassOverloadsInterfaceMethods() throws Exception {
		assertTrue(OverloadUtil.isOverloaded(returnsObjectNoParametersOnInterfaceType, returnsStringOneParameter));
	}

	public void testInterfaceImplementationIsNotOverloading() throws Exception {
		assertFalse(OverloadUtil.isOverloaded(returnsObjectNoParametersOnInterfaceType, returnsStringNoParameters));
	}

	/**
	 * This type of test should be reversible
	 * 
	 * @throws Exception
	 */
	public void testIsNotOverloadingForDifferentNamesOnSameClass() throws Exception {
		assertFalse(OverloadUtil.isOverloaded(returnsStringNoParameters, returnsObjectNoParametersDifferentName));
		assertFalse(OverloadUtil.isOverloaded(returnsStringOneParameter, returnsObjectNoParametersDifferentName));
	}

	public void testIsNotOverloadingForDifferentNamesInterfaceAgainstConcrete() throws Exception {
		assertFalse(OverloadUtil.isOverloaded(returnsObjectNoParametersOnInterfaceType,
				returnsObjectNoParametersDifferentName));
	}

	public void testOverridingIsNotOverloading() throws Exception {
		assertFalse(OverloadUtil.isOverloaded(returnsStringNoParameters, returnsStringNoParametersOnSubClass));
	}

	public void testMethodOnSubclassOverloadsInterfaceMethod() throws Exception {
		assertTrue(OverloadUtil.isOverloaded(returnsObjectNoParametersOnInterfaceType,
				returnsObjectThreeParametersOnSubClass));
	}

	/**
	 * This type of test should be reversible
	 * 
	 * @throws Exception
	 */
	public void testMethodOnSubclassOverloadsMethodOnSameClass() throws Exception {
		assertTrue(OverloadUtil.isOverloaded(returnsStringNoParametersOnSubClass,
				returnsObjectThreeParametersOnSubClass));
		assertTrue(OverloadUtil.isOverloaded(returnsObjectThreeParametersOnSubClass,
				returnsStringNoParametersOnSubClass));
	}

	public void testMethodOnSubclassOverloadsMethodOnSuperClass() throws Exception {
		assertTrue(OverloadUtil.isOverloaded(returnsStringOneParameter, returnsObjectThreeParametersOnSubClass));
	}

	public void testMethodOnSubclassDoesNotOverloadMethodOfDifferentNameOnSuperClass() throws Exception {
		assertFalse(OverloadUtil.isOverloaded(returnsObjectNoParametersDifferentName,
				returnsObjectThreeParametersOnSubClass));
	}

	/**
	 * Util method to get a method, ignoring checked exceptions
	 * 
	 * @param clazz
	 * @param name
	 * @param parameterTypes
	 * @return method
	 */
	private static Method getMethod(Class clazz, String name, Class... parameterTypes) {
		Method method = null;
		try {
			method = clazz.getMethod(name, parameterTypes);
		} catch (Exception e) {
			e.printStackTrace();
		}
		return method;
	}

}
[/java]

And finally, <strong>test fixtures:</strong>

[java]package com.robsanheim.sandbox.reflection.overloading;

public class ConcreteClass implements Interface {
	
	/** (non-Javadoc)
	 * implements the method in the interface type with a covariant return type
	 * @see com.robsanheim.sandbox.reflection.overloading.Interface#method()
	 */
	public String method() {
		return null;
	}
	
	/**
	 * Overloads method in this concrete class, does not overload method from interface
	 * @param one
	 * @return
	 */
	public String method(String one) {
		return null;
	}
	
	public Object anotherMethod() {
		return null;
	}
}[/java]

[java]package com.robsanheim.sandbox.reflection.overloading;

/**
 * @author Rob Sanheim
 * 
 * Basic interface for testing
 */
public interface Interface {
	public Object method();
}[/java]

[java]package com.robsanheim.sandbox.reflection.overloading;

public class SubClass extends ConcreteClass {
	/** 
	 * Override method from concrete class
	 */
	public String method() {
		return null;
	}
	
	public Object method(String one, String two, String three) {
		return null;
	}
}[/java]
