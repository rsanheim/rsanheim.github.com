--- 
wordpress_id: 30
layout: post
title: DWR, Tomcat 5.5, and Xalan classpath error
wordpress_url: https://www.robsanheim.com/?p=30
---
If you get errors attemtping to use DWR with Tomcat 5.5+ with a stack trace similiar to:

<code>342192658 [http-8080-Processor3] ERROR org.apache.catalina.core.ContainerBase.[Catalina].[localhost].[/Ajax]  - StandardWrapper.Throwable
javax.xml.transform.TransformerFactoryConfigurationError: Provider org.apache.xalan.processor.TransformerFactoryImpl not found
	at javax.xml.transform.TransformerFactory.newInstance(Unknown Source)</code>

It is due to an issue with the xml-apis.jar that Tomcat includes in the common/endorsed directory (which is also in the tomcat classpath by default).  This jar conflicts with the javax call attempted seen in the stack trace.  I renamed xml-apis.jar to .bak and restarted, which solved the problem, but you could probably also just remove /common/endorsed from the startup script.  I'm not sure if Tomcat needs either of the jars in this folder for its own work, but so far things seem to work fine.
