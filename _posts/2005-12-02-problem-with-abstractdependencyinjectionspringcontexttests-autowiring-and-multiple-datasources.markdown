--- 
wordpress_id: 131
layout: post
title: Problem with AbstractDependencyInjectionSpringContextTests, autowiring, and multiple datasources
excerpt: hacking AbstractDependencyInjectionSpringContextTests to autowire by type
wordpress_url: https://www.robsanheim.com/?p=131
---
NOTE: this is not needed for Spring 1.26 due to <a href="https://opensource2.atlassian.com/projects/spring/browse/SPR-1428">this fix</a> that went in.  I only had to do this because we are locked in at 1.25 right now.

I was having issues setting up some integration tests using Spring's <a href="https://www.springframework.org/docs/api/org/springframework/test/AbstractDependencyInjectionSpringContextTests.html">AbstractDependencyInjectionSpringContextTests</a> in version 1.15, and later 1.25.  After some searching around, I figured out how my issues were related to the application context always being setup by type, where I needed it by name.

Here is how you set the autowire mode to whatever you want for your transactional tests (which is basically what was added in 1.26) - this assumes you aren't using populateProtectedVariables(true), as it uses that as an extension point for this.  We have to do this since setUp is final way up in the hiearchy.

First, you should have your own base test case that extends the ATDSCT (mine is called PersistenceTestCase) that you use for database testing.  In that base class, add this:

[java]
	/**
         * set a boolean so our overriden method gets called in setUp()
	 * default constructor
	 */
	public PersistenceTestCase() {
		super();
		// have to do this hack here because we cannot set the autowire mode 
		// in Spring 1.25 and lower's AbstractDependencyInjectionSpringContextTests
		setPopulateProtectedVariables(true);
	}

	/**
	 * Override this to actually autowire things however we want 
	 */
	protected void populateProtectedVariables() throws IllegalAccessException {
		this.applicationContext.getBeanFactory().autowireBeanProperties(this, getAutowireMode(), isDependencyCheck());
	}

	/**
	 * @return autowire constant, should be a constant from AutowireCapableBeanFactory
	 */
	protected int getAutowireMode() {
		return AutowireCapableBeanFactory.AUTOWIRE_BY_TYPE;
	}
[/java]

You could also do all this stuff in your spring config xml for testing, btw.
