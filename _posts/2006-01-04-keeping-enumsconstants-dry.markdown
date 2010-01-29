--- 
wordpress_id: 153
layout: post
title: Keeping enums/constants DRY?
wordpress_url: http://www.robsanheim.com/?p=153
---
I'm pretty sure there is no way to do this with <a href="http://jakarta.apache.org/commons/lang/api/org/apache/commons/lang/enum/Enum.html">Commons Enum</a> (yes, I'm stuck on 1.4) using plain ole java.  Say you just want every enum to have the same attribute name as its variable name, like so:

[java]
        private static int index = 0;
        private final static SalesOrgType DISTRICT = create("DISTRICT");
	private final static SalesOrgType SALES_STATE = create("SALES_STATE");
	private final static SalesOrgType CORPORATE = create("CORPORATE");
	private final static SalesOrgType REGION = create("REGION");

	private static SalesOrgType create(String name) {
		return new SalesOrgType(name, index++);
	}[/java]

...without specifying the name of the enum twice in each declaration?  I.e. if I create an enum var as FOO, I want it to be created with "FOO" passed in to the constructor for the name?

You also see this pattern often in String constants:

[java]public final static String USER_KEY = "USER_KEY";[/java]

Annoying.  I'm guessing the only pure java solution would be to declare your variables, then reflectively look for everything of type x in the class and get their names.  Then call setName with the field name of each thing.  This would break your immutability and would be hackish and complex to boot.
