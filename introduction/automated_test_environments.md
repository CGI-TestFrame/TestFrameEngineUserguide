## Automated test environments

The figure below sketches an abstract picture of an automated test environment in which TestFrame is applied.

![Figure 1](TFEBuildingBlocks.jpg)

An automated test environment using TestFrame, in seven parts:

1.	SUT, the system under test;
2.	CLUSTER, a tab separated file specifying the actions of the test, written in the action word based TestFrame Language;
3.	REPORT, a document containing the results of the test; 
4.	ACTIONS, the test specific software automating the test actions; 
5.	ENGINE, the TestFrame Engine linking together cluster, report and test software; 
6.	WRAPPER, the test tool specific interface to the Engine; 
7.	INTERFACES, the interfaces to the SUT used by the test software.


TestFrame's basic premise - the separation between analysis and navigation - grew out of the desire to overcome the limitations of record-and-playback tools. These tools were, and still are, used to create test software. They contain standard interfaces to certain types of applications - most of them mainly to GUI applications. They can record actions performed on the SUT - generating scripts with the used interfaces and data. These scripts can then be run to replay the actions. But if an action differs only slightly from another one - e.g. typing "B" instead of "A" in some field of an administrative SUT - a whole new test script is required for playback by these tools.

To improve this situation, TestFrame takes the test data out of the scripts and places it in other files - the clusters; furthermore, it places the test results in files outside the test software as well - the test reports. By doing so, specification and implementation have been separated.

To be able to let test tools—or more general: test software — get test data from clusters and write results to reports, there must be software that is able to do this. This software is the Engine, the user’s guide to which you are now reading. The functionality of the Engine can be used by the test software via interface functions. Not only by scripts in various test tools, but by almost any piece of software. So, on any SUT to which interfaces exist, automated tests using TestFrame can be performed. (Since any system which does not have interfaces isn’t of use to anyone, it can be said: all SUTs.) Because, if no tools exist which support the SUT’s interfaces, software can be developed which does. This interfacing software—written in C, Java or whatever language—can implement the necessary test actions and interface with the Engine via its interface functions to process and report the tests.

The interface functions of the Engine are the same in any environment and on any platform. This creates the added advantage that all test automation with TestFrame uses the same standard. A project testing on a Windows XP PC a GUI application with Quick Test Pro has as its basis the same structure as a project testing an embedded system via a parallel cable from a UNIX workstation using software written in C.

In the test environment model it is clear that besides separating the Engine, the remaining test software is divided into three parts: the interfaces to the SUT; the actions, which comprise the project specific test software—the implementations of the user defined action words; and a third module, the wrapper.

The wrapper contains the generic part of the test software which deals with test processing. It is a test software language specific “shell” around the Engine (hence the name wrapper). Its purpose is to offer the Engine’s functions to the actions module, and be the Engine’s active counterpart. The Engine has been built as a passive program—primarily because of most test tools’ property to take complete control of the machine on which they run. This control means the initiative must be taken by software in the tools. So the wrapper takes these initiaves: calling on the Engine to process the cluster until it finds a test action, then calling on the actions module to execute this action, then returning to the Engine again.

At this moment wrappers are available for some of the most well known test tools: Quick Test Pro® by HP™, QARun™ by Compuware®, Rational Robot™ by IBM®, WinRunner by HP and also for the programming languages, Visual Basic, C/C++ and Java. Wrappers for SilkTest(Borland), TestComplete(Automated QA) and Rational Functional Tester(IBM) are in development.

When installing the TF Engine, wrappers for WinRunner, QARun, C/C++, Java and Visual Basic are installed by default. Other wrappers can be requested by sending an email to ccctesting@logica.com. 

Traditional GUI based information systems will most likely still be tested using one of the standard test tools. In those cases, the three modules of test software will all be part of this tool: the interfaces to the SUT provided by the tool’s manufacturer, the actions and wrapper as scripts written in the tool’s scripting language.

Technical systems—basically all non-GUI applications—will be tested using special tailored software, since test tools offer no solutions. The interfaces—in technical systems more diverse and specific—the actions and the wrapper will all be programmed individually—in the same, or different programming languages.
