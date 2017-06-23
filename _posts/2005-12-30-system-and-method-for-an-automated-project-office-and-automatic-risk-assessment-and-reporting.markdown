---

title: System and method for an automated project office and automatic risk assessment and reporting
abstract: In the automation of project risk identification, various qualitative and quantitative measures are combined to report a project's risk level, areas, and mitigation in an automatic and objective manner. The software package includes a risk assessment and report framework and a risk engine, a portfolio analysis, a project plan validator, an integrated project management office toolkit and process asset library, and an integrated skills tracking, locating and availability module with a skills engine.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08041647&OS=08041647&RS=08041647
owner: Computer Aid Inc.
number: 08041647
owner_city: Allentown
owner_country: US
publication_date: 20051230
---
The present application claims the benefit of U.S. Provisional Patent Application No. 60 640 104 filed Dec. 30 2004 whose disclosure is hereby incorporated by reference in its entirety into the present disclosure.

Related disclosure is found in U.S. Provisional Patent Application No. 60 618 231 filed Oct. 14 2004 and in U.S. patent application Ser. No. 11 249 744 filed Oct. 14 2005 whose disclosures are hereby incorporated by reference in their entireties into the present disclosure.

The present invention is directed to a system and method for automation of project risk identification and in particular to such a system and method in which various qualitative and quantitative measures are combined to report a project s risk level areas and mitigation in an automatic and objective manner.

In Project Management Essentials from MetaGroup a statistical survey was conducted for 23 000 application development projects. The following results were projected 

The researchers found that the core issues with project success were mostly related to poor project management discipline. The root cause or underlying problem often is attributable to poor project estimating techniques ineffective project team structure team risks a lack of client end user participation unmanaged scope changes and taking on large scale project risks without any contingencies.

Project management software was brought along to address these problems but often fails to do so effectively.

It is therefore an object of the invention to overcome the above noted deficiencies of the prior art. To that end the present invention is directed to a system and method that in various embodiments can include the following functionalities.

The Risk Assessment and Report Framework combines various project performance measurements as well as a comprehensive set of multifaceted questions to be processed by a risk engine to assess a project s level or risk and the areas where risk exists. In addition to identifying risks advice on mitigation of the identified risks as well as tracking of mitigation actions is performed to enhance the system s ability to assess and provide future risk advice.

The framework collects data either through Application Program Interfaces APIs or via direct data entry on project performance measured by base Earned Value Analysis EVA data quality data on defect rates customer satisfaction ratings manpower utilization milestone progress. The risk engine uses the inputs to evaluate the performance against warning thresholds and limits to identify and report trouble. In the case of EVA a set of performance indicators are calculated from the main performance input to determine schedule and cost performance as well as the level of risk and recoverability of the schedule and cost.

In addition to the performance metrics and thresholds the risk engine uses data from question sets that survey various aspects of the projects activities to assess risk in various areas. Each question set and possible answers are categorized scored and weighted in such a way as to identify potential risk areas and these risks are then reported via a dashboard to the user.

Questions sets are formed from a large question pool that contains all possible questions risk categories answers and scores. New question sets are built by selecting questions from the pool and storing the question set into a question set library. The risk identification is broken down into several levels of classification and increasing detail according to a risk structure of risk categories that each category contains risk areas and that each risk area contains risk attributes. Each question in the question pool is assigned to a particular risk attribute thus when incorporated into a question set it becomes part of the risk engine s risk calculation.

The question sets are customizable and are assigned according to various classifications for a project. Classifications for the project include a portfolio and a project type. Projects are broken down into one or more portfolios or collections which have some common characteristic or interest for example a business unit or line of business or a particular technology etc. . Each portfolio has one or more question sets assigned to it that are used for assessment the elements of risk via the risk engine for all projects belonging to that portfolio. In addition to the portfolio assigned question sets there are project type questions sets. Each project has a type classification assigned to it and that type automatically incorporates risk question set appropriate for the particular project type. In addition to these two question set associations each project can add any additional or supplemental question sets as needed to expand the risk assessment coverage.

In addition to the portfolio project type and supplemental question sets the risk engine provides for a role association for the question sets at each of those levels. The roles allow users with different roles responsibilities to provide input to the risk engine and have those perspectives combined into an overall risk assessment and to identify differences in views for establishing consensus within a project. The roles can include but are in no way limited to a Project Manager a Quality Engineer or a Project Sponsor.

The risk engine provides a facility for periodically running or stepping through the question sets for each project. The risk engine assembles the question sets eliminates any duplication or overlap between question sets as different question sets can share any number of questions from the larger question pool and present a user with an orderly unique questionnaire. Users are required to periodically go through the question sets to update the risk assessments and to provide risk trend analysis. Each user that has a particular role for a project creates an answer session for the questionnaire and is presented with all questions appropriate for the role portfolio project type and supplemental questions. Once all questions have be satisfactorily answered the answers are submitted and the risk engine computes and updates the risk assessment for the project.

The risk engine combines the risk assessment scores and metric scores from the EVA quality customer satisfaction manpower and progress and reports those on a project or portfolio dashboard using a stop light kind of indicator green yellow amber red to indicate an overall level of risk. The overall risks can be drilled down on via a web browser based interface to display increasing levels of detail of the risk status. This drill down continues to the level of the questions and answers or metrics that are driving the overall status. Where risks have been identified by the risk engine mitigation advice is made available to the user to identify actions to take that are appropriate to mitigate each risk.

Along with the mitigation advice is a mechanism for recording and tracking the mitigation actions taken and the results of those actions for automatic incorporation into the mitigation advice to provide heuristics to the mitigation component of the risk engine providing all projects with improved mitigation advice as the risk engine continues to collect data.

The Automated Project Office APO integrates a Portfolio Analysis function that allows an organization to track its projects according to a high level classification system that allows for understanding a particular project footprint or balance of efforts relative to an overall goal. In particular the preferred embodiment incorporates the MIT Model of portfolio classification and uses it to perform a classification balance analysis although those skilled in the art who have reviewed the present disclosure will appreciate that other models can be used instead of or in addition to the MIT model. For example the MIT Model classifies projects as Infrastructure Transactional Informational or Strategic and uses the relative distributions of projects to those classifications to determine a position or balance for Cost Focused portfolio Agility portfolio or Balanced Cost and Agility portfolio. Through the APO and organizations portfolio of projects can be tracked and measured according to the target position desired.

In addition to the MIT Model for portfolio classification a user can create new models with any classifications desired and use them in the same way as the MIT Model. A project can be assigned as many portfolio portfolio classifications as desired and have all tracked and reported via a common dashboard via a web browser.

The APO integrates a Project Plan Validator facility using project heuristics to measure proposed project plan efforts by phase against known plan performance statistics for general project phases to determine if the plan contains the right work breakdown and effort distribution. Using the validator a project manager can quickly see if too much or too little time has been allocated to critical phases of the project and make adjustments before the plan is baselined and commitments are made for delivery dates. The validator uses statistics from completed projects to set the distribution of effort for a particular kind of project and can then be given for example a single number covering a single element from a plan and determine the efforts by phase and total effort necessary for the project to be completed.

The APO integrates a Project Management Office PMO Toolkit and Process Asset Library PAL . The toolkit provides essential documents and templates that correspond to PMO best practices and additionally is coupled with the risk engine s mitigation advise to ensure the tools for risk mitigation are given additional visibility and tracking in the APO. The integrated PAL allows documents and tools used by other APO projects to be shared and their usage automatically tracked by the APO to provide powerful means of identifying organizational best practices and tools. The tracking allows for locating high value high usage items and pruning of low value unused items at appropriate time.

The Skills Engine of the APO provides a facility for tracking an organization s or sub unit s of the organization s people resources. The Skills Engine provides first and inventory of all skills within the organization or sub organization using the APO. Beyond the skills inventory the engine provides tracking of the resources and skills assigned to projects and with a view toward when the resources and associated skills will be available for further allocation as well as aiding in reallocation of skills and resources to other projects. The Skills Engine provides for a skills search facility to locate resources with the skills needed for a project. In addition to the location of resources with needed skills the engine allows for those resources to have a claim placed on them. The claim facility can either be hard or soft. A hard claim can be made for resources being placed on a project that has been contracted and has a start assigned. A soft claim is made for resources for a project that is not formally committed to but allows for identification of intent to utilize particular resources in the future. This capability of the engine gives managers and project managers a facility to identify what resources are to be used and to act early on allocation of resources resolution of resource conflicts and identification of new resources with particular skill that need to be obtained.

The skills engine also provides a tracking of overall availability of the resources and skills in the organization with notifications and warnings for resources who are under allocated relative to their defined availability or not allocated at all. As part of this engine s processing and outlook for the utilization that looks into the future alerts managers of upcoming under utilization which provide a means to avoid lost organizational productivity because the resource might otherwise be left idle.

A preferred embodiment will be disclosed in detail with reference to the drawings in which like reference numerals refer to like elements or operational steps throughout.

An overview of the functionality of the preferred embodiment is shown in the use case diagram of . The user supplies project plan statistics to a project plan validator which returns effort distribution validation to the user . The integrated project management office toolkit process asset library supplies information to the user . The user supplies information on the skills and availability of workers as well as searches and claims for such workers collectively designated to a skills engine which returns information on resource and skill availability tracking notification and alerts to the user .

The user interacts in the following manner with the risk engine . The user forms custom questions answers and thresholds into a question set which becomes one of the user defined and pre packaged question sets used by the risk engine . The user supplies the following input to the risk engine earned value analysis EVA question responses performance measurements quality data customer satisfaction information staff power utilization information and milestone progress . Also an external data gathering application can gather data from the user and supply such data to the risk engine through an application programming interface API .

The results of the operations performed by the risk engine are output to the user through one or more dashboards which are user interfaces that provide such results in visual form. The risk engine determines schedule and cost performance and levels of risk and recoverability and outputs them in the form of the EVA output to the dashboards . The risk engine determines potential risk areas and risk mitigation advice and outputs them in the form of risk reporting to the dashboards . The risk reporting can also include input directly from the user . The risk engine can output an overall risk output to the dashboards the overall risk output can include a stop light indication for display on the dashboards if the level of risk warrants it. The risk engine outputs information to a portfolio analysis which can be standard or user defined which is output to the dashboards .

The functionality shown in and described above is implemented on a Project Office Data System PODS shown in as . The PODS is centered on a Project Management Office PMO database which stores among other things assessment questionnaires . The database receives information on projects and skills and allows reporting and querying by management and subject matter experts SME s .

The operations of the preferred embodiment will now be explained with reference to . shows a flow chart of the operations of the preferred embodiment. shows a main screen flow chart. shows an administration screen flow chart. shows a project initiation screen flow chart. shows an active project screen flow chart. shows a flow chart of the reports.

The PODS application Login page protects the application and its resources from being accessed by unauthorized users. Only Active users are allowed to access the application. To access the application the user is required to provide his her login name and password. The login page is located in the root directory.

The login page is where the user types in his or her login name and password to gain access to the PODS application. The user can specify whether after successful login to show first the password maintenance page to update his or her current password. This can be accomplished by checking the checkbox Change my password after successful login before clicking on the Login button. If this is not checked after successful login the user is transferred instead into the home page .

If the user typed in an invalid login name or password the login page would display the message Invalid Login name Password combination to inform the user.

To validate the password supplied by the user retrieve the hashed password string in the database for the login name supplied. Remove and keep the 2 salt characters from the hashed password string retrieved. Add the salt characters to the front of the password string supplied by the user to make a new password string. Use MD5 algorithm to hash the new password string into a new hashed password string and convert it to an ASCII hex string creating a new hexified password string. Compare the new hexified password string to the hashed password string retrieved from the database. If the passwords match the user is allowed to access the application otherwise the password supplied is invalid and login is denied.

The home page also known as the Portfolio Summary View Page is displayed upon successful login. It contains two table summaries Active Projects and Completed Projects. These tables show a general overview of the status of the different projects. The Active Projects table displays ongoing projects. The Completed Projects table displays finished projects. By default the projects in the both tables are sorted by project name in ascending order. The data in both tables can also be sorted ascending order by column headings.

The Home page Portfolio Summary view provides a list of Active Projects and Completed Projects sorted by Project Name at the outset upon loading. The User has the option to sort the tables by clicking on the column headings. The content of this page is retrieved from the different tables in the database.

The home page is located in the root directory and is protected through user authentication. All users are allowed to view this page once they have been authenticated and session is still valid.

The Create New Project page allows the user to define a new project. Both the Project Name and description are required fields. The project ID is automatically generated upon creation of a new project.

The Create new project page is located in the root directory and is protected through user authentication. All users are allowed to view this page once they have been authenticated and session is still valid.

The View Existing Project page lists the Active Projects and Completed Cancelled Projects based on the search criteria defined by the user. If no search criteria is selected it will display the projects grouped by Active and Completed Cancelled status once the user clicks on the search button. To view Project details the user simply double clicks the preferred project and he she will be redirected to the Project Initiation General page.

The View Existing Project page serves as a facility to filter projects by Customer Project Manager or Project Type. The Completed Cancelled Projects list enumerates all projects that were finished or were called off. The Active Projects list enumerates all ongoing projects. All projects in both lists can be double clicked to show the page that corresponds to the current phase of the project.

The view existing project page is located in the root directory and is protected through user authentication. All users are allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation General page permits the user to define or update the Project Initiation General details of a new or existing project. The save button will appear for projects whose Project Initiation General information has not yet been defined. Otherwise an update button will appear. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the fields have been filled up. After saving the data in the database and if all the fields in the page have been filled up the user will be asked if he wants to proceed to the next page or go back to the home page.

This page is located in the data attributes directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Assessment page permits the user to define or update the Project Initiation Assessment details of a new or existing project. The save button will appear for projects whose Project Initiation Assessment information has not yet been defined. Otherwise an update button will appear. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the fields have been filled up. After saving the data in the database and if all the fields in the page have been filled up the user will be asked if he wants to proceed to the next page or go back to the home page.

This page is located in the data attributes directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Assessment page provides users the facility to define and or update general project assessment information. A set of determinants are presented together with a set of possible answers to which the users can select from. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose General Project Assessment information has already been defined.

The Project Initiation Assessment Human Resources page permits the user to define or update the Project Initiation Assessment Human Resources details of a new or existing project. The save button will appear for projects whose Project Initiation Assessment Human Resources information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Project Initiation Assessment Human Resources page provides users a series of questions regarding the Human Resource aspect of a new project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose Project Initiation Assessment for Human Resource information has already been defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Assessment Quality page permits the user to define or update the Project Initiation Assessment Quality details of a new or existing project. The save button will appear for projects whose Project Initiation Assessment Quality information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Project Initiation Assessment Quality page displays a set of questions regarding the Quality aspect of a new project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose Project Initiation Assessment for Quality information has already been defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page will be located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Assessment Risk page permits the user to define or update the Project Initiation Assessment Risk details of a new or existing project. The save button will appear for projects whose Project Initiation Assessment Risk information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Project Initiation Assessment Risk page displays a set of questions regarding the Risk aspect of a new project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose Project Initiation Assessment for Risk information has already been defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page will be located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Assessment Schedule page permits the user to define or update the Project Initiation Assessment Schedule details of a new or existing project. The save button will appear for projects whose Project Initiation Assessment Schedule information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Project Initiation Assessment Schedule page displays a set of questions regarding the Schedule aspect of a new project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose Project Initiation Assessment for Schedule information has already been defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Assessment Scope page permits the user to define or update the Project Initiation Assessment Scope details of a new or existing project. The save button will appear for projects whose Project Initiation Assessment Scope information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Project Initiation Assessment Scope page displays a set of questions regarding the Scope aspect of a new project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose Project Initiation Assessment for Scope information has already been defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Baselines page permits the user to define or update the Project Initiation Baselines details of a new or existing project. The save button will appear for projects whose Project Initiation Baselines information has not yet been defined. Otherwise an update button will appear. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the fields have been filled up. After saving the data in the database and if all the fields in the page have been filled up the user will be asked if he wants to proceed to the next page or go back to the home page.

The Project Initiation Baselines page serves as a facility where users can define and or update information like planned start date planned hours budget and planned staffing size for each phase of a project. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for newly defined projects while the Update button appears for projects whose Project Initiation Baseline information has already been defined.

This page is located in the data attributes directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project General page permits the user to define or update the Active Project General details of an active project. The save button will appear for active projects whose Active Project General information has not yet been defined. Otherwise an update button will appear. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the fields have been filled up. After saving the data in the database and if all the fields in the page have been filled up the user will be asked if he wants to proceed to the next page or go back to the home page.

This page will be located in the data attributes directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project General page displays the details and basic information of an active project. This serves as a facility where each detail item can be updated to reflect current changes in the status of the project still active completed cancelled project cost to date and others. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for active projects whose general information has not yet been defined while the Update button appears for active projects whose general information has been previously defined.

The Active Project Cost page permits the user to define or update the Active Project Cost details of an active project. The save button will appear for active projects whose Active Project Cost information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Active Project Cost page displays specific questions regarding the Cost aspect of an active project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button The Save button appears for active projects whose cost information has not yet been defined while the Update button appears for active projects whose cost information has been previously defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project Human Resources page permits the user to define or update the Active Project Human Resources details of an active project. The save button will appear for active projects whose Active Project Human Resources information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Active Project Human Resources page displays specific questions regarding the Human resources aspect of an active project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for active projects whose human resources information has not yet been defined. The Update button appears for active projects whose Human Resources information has been previously defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project Quality page permits the user to define or update the Active Project Quality details of an active project. The save button will appear for active projects whose Active Project Quality information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Active Project Quality page displays specific questions regarding the Quality aspect of an active project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for active projects whose Quality related information has not yet been defined. The Update button appears for active projects whose Quality related information has been previously defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project Risk page permits the user to define or update the Active Project Risk details of an active project. The save button will appear for active projects whose Active Project Risk information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Active Project Risk page displays specific questions regarding the Risk aspect of an active project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for active projects whose Risk related information has not yet been defined. The Update button appears for active projects whose Risk related information has been previously defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page is located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project Schedule page permits the user to define or update the Active Project Schedule details of an active project. The save button will appear for active projects whose Active Project Schedule information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Active Project Schedule page displays specific questions regarding the Schedule aspect of an active project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for active projects whose Schedule related information has not yet been defined. The Update button appears for active projects whose Schedule related information has been previously defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page will be located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project Scope page permits the user to define or update the Active Project Scope details of an active project. The save button will appear for active projects whose Active Project Scope information has not yet been defined. Otherwise an update button will appear. There is a score corresponding to a question answer combination which will be used to determine the color classification to be displayed in the reports. The user can save the data in the database at any point at any level of completion but can only advance to the next page once all the questions have been answered. After saving the data in the database and if all the questions in the page have been answered the user will be asked if he wants to proceed to the next page or go back to the home page.

The Active Project Scope page displays specific questions regarding the Scope aspect of an active project. A set of answers for each question are presented but only one can be selected. There are two 2 buttons at the end of the page. These are the Save Update button and the Clear button. The Save button appears for active projects whose Scope related information has not yet been defined. The Update button appears for active projects whose Scope related information has been previously defined.

The contents of this page are dynamically loaded based on the data retrieved from the different tables in the database based on the category. This page will be located in the questionnaires directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Password Maintenance page shown twice in for ease of following allows all types of users to update his her password after a successful login provided that they have clicked on the Change Password option from the login page . The password page will be located in the root directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Security page allows the security SEC privileged users to update the password of other users using the Password maintenance page and to add update or delete deactivate only in the database a user using the User maintenance page . For the Password Maintenance page all fields are required to be filled up by the user. For the User maintenance page all fields are also required to be filled up when adding or updating user information. The Login ID is automatically generated upon creation of a new user. To delete a user simply set the Active Status to No. For non SEC privileged and non ADMIN privileged user set the Admin and Sec privilege flag to No respectively.

The Security page contains the Password and User Maintenance tools and is only accessible for users with the SEC privilege. The User Maintenance feature provides SEC privileged users the functionality to add update or delete deactivated only in the database users. To update or delete a user simply enter the login name and click the search button to retrieve user data then make the necessary changes and click the save button to update changes. To add a user fill up all the required fields and click the save button to add the user. The Password Maintenance feature provides SEC privileged users the functionality to change other user s passwords.

The password field will be hashed using the MD5 algorithm before saving the data in the database. To store a password in the database a random set of two salt characters will be generated and added to the front of the password supplied to make a new password string. The new password string is then hashed using the MD5 algorithm to obtain a new hashed password string converted to an ASCII hex string creating a hexified password string. The salt characters are then added to the front of the hexified password string and then stored in the database.

The security page will be located in the root directory and is protected through user authentication. Only users with SEC privileges will be allowed to view this page once they have been authenticated and session is still valid.

The Add Customer Manager page allows ADMIN privileged users to add a customer or project manager. To add a customer simply fill in the customer name and click on the Enter customer button. The customer ID is automatically generated upon creation of a new customer. To add a project manager fill in the project manager first name and last name and click on the Enter Project Manager button. The project manager ID is automatically generated upon creation of a new project manager.

The Add Customer Manager page is only accessible to users with the ADMIN privilege. The Add Customer function allows ADMIN privileged users to add a new customer to the system. The Add Project Manager function allows ADMIN privileged users to add a new project manager to the system.

This Add Customer Manager page will be located in the root directory and is protected through user authentication. Only users with ADMIN privileges will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Summary Report page allows users to filter the newly initiated project reports not yet active by Customer Name Project Name Project Manager and Project Type. The user also has the option to select which type of Project Initiation report to generate the available options include Identification Team Dynamics Assessment Info report Project Stated Risk Info report and Planned Project Baseline Info report . After selection clicking on the Create Report button initiates creation of an online report. Clicking on the Clear button resets to default values all the input controls.

The Project Initiation Summary Report allows users to filter the newly initiated project reports not yet active by Customer Name Project Name Project Manager and Project Type. The user has also the option to select which type of Project Initiation report to generate. The available Project Initiation reports include Identification Team Dynamics Assessment Info Project Stated Risk Info and Planned Project Baseline Info.

This page will be located in the reports directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Initiation Identification Team Dynamics Assessment Report shows the general assessment of the project in terms of Schedule Scope Risk Human Resources and Quality. Assessments are based on the information provided by the users from the Project Initiation pages.

The Project Initiation Project Stated Risk Report shows the assessment of potential risk items per project. This includes Technology Delivery Date Quality Customer Satisfaction Constraints and other miscellaneous risk items including Critical Success Factors to be observed both for the customer and the developing organization.

The Project Initiation Planned Project Baseline Report shows planning values which include start date end date hours budget and staff size for each phase of a project.

The Project Initiation Details Report serves as the facility for users to select a specific project to which different information which include Constraints Risk Critical Success Factors for Customer Critical Success Factor for Developing Organization Technologies Asset Requirements Special Communication Requirements and Other Comments can be viewed instantaneously.

This page will be located in the reports directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Active Project report page allows users to filter the active project reports by Customer Name Project Name Project Manager Project Type and Status. There is an option to select which type of Project report to generate. The available reporting options include Identification Project Details Project Management Info Analysis and Business Design Planning vs. Actual Technical Design and Construction Planning vs. Actual Testing and Implementation Planning vs. Actual and Assessment.

This page is located in the reports directory and is protected through user authentication. All users will be allowed to view this page once they have been authenticated and session is still valid.

The Project Identification Project Details Project Management Report shows merging values from the identification and project details report and the project management information report. Issue tracking report values are included.

The Project Analysis Business Design Report displays Planned values compared against Actual values for Start Date End date Hours Budget and Staff Size of the Analysis and Business Design phases of active projects.

The Project Technical Design Construction Report displays Planned values compared against Actual values for Start Date End date Hours Budget and Staff Size of the Technical Design and Construction phases of active projects.

The Project Testing Implementation Report displays Planned values compared against Actual values of Start Date End date Hours Budget and Staff Size of the Testing and Implementation phases of active projects.

The Project Assessment Report displays comparisons between current and previous assessment of Schedule Scope Risk Human Resources Quality and Cost of active projects.

Additional details on the functionality of the preferred embodiment will now be set forth. Language like needs must and requires refer to the preferred embodiment only and are not intended nor should they be construed as limitations on the invention as a whole.

Security for the PMO provides for user authentication as well as authorization for data entry update and reporting.

The ability exists to log and track the users that log in to and use the PMO in order to monitor utilization.

The PMO has a tailorable question pool that can be adjusted for each organization using the PMO. A base question pool with the capability to select or reject the use of various questions is included in the product. In addition to the global question pool a mechanism for adding new organization specific questions must be available. The definition of new questions must support the risk analysis and health reporting the same as if the questions are part of the base question pool.

Questions are tiered layered as well as classified according to the project type. Each project is given a tier control level that dictates the question depth. The line of questioning is controllable at both a project and a global level allowing the question depth to be set with the project. The questions are also dictated by the project type and the classification of each question according to project type e.g. new development questions are only be presented for projects that are classified as new development level 2 or deeper questions are only be presented for projects which have be set to that level or deeper .

All questions are assigned levels project types risk categories life cycle timing risk factors for each possible answer and reactions to answers including but not limited to If other questions will be opened or closed if status will change and if a notification will be activated all depending on certain answers.

The Question Pool has a Maintenance function built into the program that allows for creating changing and removing questions from the Pool. This function will be open only to users with certain access permissions and will allow the end user to manage and create their own questions as well as the pre packaged question set. This includes notifications that will detail any continuity issues that may arise when a question is deleted. There is also some consideration as to predicting potential conflicts between questions as new ones are added to the system.

The user can create custom questions sets that will apply to certain project types. In order to accomplish this there needs to be a system to allow for the dynamic building of question sets from the complete question pool. This system can identify relationships between questions so that when the user goes to save their new question set they can be notified if they picked one question from the middle of hierarchy of questions that there are other questions that should come with it.

The Maintenance function contains a function that will allow for the display of the different question sets based upon which project type they are assigned to. A user would come to this section select a project type and the program displays the list of questions that are assigned to that type.

The Maintenance function has a Periodic Review section. This is based off of the date created field attached to each question. The user will select an interval at which Questions will be marked for review showing that the questions should be revisited to determine if they are still applicable or need to be edited. Once they have reviewed and updated if necessary they will be able to mark the question as approved and it will not be flagged until the interval has passed again.

The Project Profile and Inventory provides a list of all projects under the PMO and profiles describing general and some technical aspects of each project. Use of the inventory provides information on past and current projects their results and allows comparison of project performance with other projects based on profile information.

The system has a means of adding updating and deleting project profile information by properly authorized users. Each operation add update delete is discretely assignable to authorized users.

The project asset classes are based on the MIT model for classification. The meanings of the classes are described below.

Infrastructure provides a shared standardized capability base for the enterprise. Infrastructure projects lead to greater business flexibility and integration. Infrastructure investments are moderately risky because of their technologies typically long life spans and technical uncertainty.

Transactional initiatives process and automate the basic transactions of the company. They intend to reduce costs and increase productivity. Usually these kinds of projects have and internal rates of return between 25 and 40 percent. These investments have the least risk of the four classes.

Informational systems provide information for managing the company. Their payoff comes from shorter time to market superior quality and the ability to set premium prices. They are moderately risky because companies often have difficulty acting on information to generate business value.

Strategic systems are typically external facing. Payoff is in sales growth competitive advantage and stronger market positioning. These are high risk. Typically 10 will have great results but 50 will not break even.

There is the ability to Custom Define a new Project Asset Class scheme as well as edit the Pre Packaged solution in case the original system does not fit the user s business or in case they already have a pre existing method to handle this data.

The program has functionality that will allow and manage the situation where two or more projects combine into one project at any given point in the projects life cycles.

The adverse also needs to be handled where the situation occurs that one project splits into multiple separate projects.

Performance tracking provides information over the life of a project as to how it is performing against task completion costs schedule milestones quality and customer satisfaction. The tracking uses defined thresholds and indicators to identify when a performance area is showing signs of trouble and coupled with the risk analysis helps to determine not only when action is needed but what kind of action as well. Performance tracking requires storing data attributes measurements and sets of measurements for each project.

The PMO must support integration with Tracer or integration with Microsoft Project as a means of automating appropriate data gathering and calculations and it must also support manual stand alone data collection.

The Earned Value Management measures tracked in the performance data are key indicators showing the performance of the project as well as providing budget and schedule projections for the project. Earned value management is based on the following general measurements.

Planned Value formerly Budgeted Cost of Work Scheduled or BCWS the cost of the work scheduled or planned to be completed in a certain time period according to plan.

Earned Value formerly Budgeted Cost of Work Performed or BCWP the planned cost of the work done up to a defined point in the project.

Actual Cost formerly Actual Cost of Work Performed or ACWP the actual cost of work up to a defined point in the project.

Averaged Average over a recent period of time up to the SD. For example 3 month and 6 month averages are meaningful between 25 and 100 completion for a project of adequate size to allow such durations shorter duration projects can use smaller periods of time like 1 and 3 month averages. The cumulative SPI is given the identifier SPI while the averaged SPI is given identifiers SPI SPI SPIfor 1 3 and 6 month averages respectively.

Cost Performance Index CPI This is the inverse of the performance ratio AC EV used by CAI. Answers Is the project on budget .

Averaged Averages over a recent period of time up to the SD. For example 3 month and 6 month averages are meaningful between 25 and 100 completion for a project of adequate size to allow such durations shorter duration projects can use smaller periods of time like 1 and 3 month averages. The cumulative CPI is given the identifier CPI while the averaged CPI is given identifiers CPI CPI CPIfor 1 3 and 6 month averages respectively.

Cost Schedule Index CSI . Also know as the Critical Index. CSI CPI SPI. The farther from 1.0 the index is the less likely the chances of recovery. Specifically 

The CSI is either a cumulative CSI or an averaged CSI depending on which SPI and CPI are used. The choice of the SPI and CPI for the calculation must be the same they will either be the cumulative or one of the same averages e.g. it is incorrect to use SPIand CPI 

Estimate At Completion. The calculated estimate for the project budget needed to complete the work based on project performance indexes 

The index can be any one of the SPI CPI or CSI. Preference is for CPI or CSI. CPI gives the most likely EAC and CSI gives a pessimistic EAC. Both the cumulative or averaged index can be used and it is useful to be able to compare indexes to each other to establish a small range of possible outcomes.

Forecast At Completion Calculated estimate for the project budget needed to complete the work. This is traditionally the way many projects forecast the cost. The EAC is a better indicator FAC is typically very low in its forecast .

Variance At Completion The calculated variance of the project s forecasted completion vs. the budgeted completion

To Complete Performance Index Baseline Required cost performance to meet the baseline original budget .

Improvement Ratio Baseline Required cost performance improvement to meet the baseline original budget given by

Estimated Completion Date Estimated date when the work will be completed based on schedule performance given by

Automatic risk analysis and reporting based largely on research by the SEI reported in the document CMU SEI 93 TR 6 published by Carnegie Mellon University June 1993 hereby incorporated by reference in its entirety into the present disclosure . Using question responses and quantitative data attributes from projects risk factors are be automatically assessed reported and tracked for each project.

Each Question and data attribute has an assigned risk category and is assigned a risk weight that can be with positive or negative. The risks are aggregated into the categories defined in SEI 93 TR 6 and used to provide an assessment of the areas of risk in the project.

The risk analysis also provides guidance on both mitigating avoiding certain risks and guidance on addressing realized risks. Mitigation strategies are taken from Capers Jones work ISBN 0 13 741406 4 hereby incorporated by reference in its entirety into the present disclosure .

The question pool is tiered so that the level of detail in the questioning for a project can be adjusted to an appropriate level.

Each question and data attribute is assigned a risk factor either based upon a particular answer or particular value. These factors are combined to produce a risk score in each area of risk classification.

The Risk Analysis is reported as part of the Health and Status Analysis giving a stop light Green Yellow and Red indicator of each of the risk areas. The indicator can be clicked on to drill down to see the elements that make up that risk value. Each risk element can also be drilled down into to see more and more detail about the risk. In addition each risk element provides guidance on risk mitigation approaches.

The risk classifications assigned to each question and attribute are those used for aggregating information related to the software risks as identified in document CMU SEI 93 TR 6 .

Each classification is broken down into a set of elements that further organize the questions and attributes. Each element is then broken down to a risk attribute. The following subsections show the structure.

Requirements cover both quality of the requirements and the difficulty of implementing a system that satisfies the requirements.

Do the requirements specify a product larger more complex or requiring a larger organization than is in the experience of the company 

Design covers the design and feasibility of algorithms functions or performance requirements and internal and external product interfaces.

Code and Unit Test deals with the quality and stability of software or interface specifications and constraints that may present implementation or testing difficulties.

Integration and Test covers integration and test planning execution and facilities for both the contractual product and for the integration of the product into the system or site environment.

Engineering Specialties covers special requirements that are usually addressed by specialists and those often on a part time basis for the project.

Are the security requirements more stringent than the current state or the practice or project experience 

The Development Process refers to the process by which the project proposes to perform the work specified by the requirements.

Is the software development process enforced monitored and controlled using measurements Are distributed development sites coordinated 

Are the project members experienced in use of the process Is the process understood by all staff members 

The Development System addresses the hardware and software tools and supporting equipment used in product development.

Are the definition and acceptance requirements defined for delivering the development system to the customer budgeted 

The Management Process deals with risks associated with planning monitoring and controlling budget and schedule controlling factors in defining implementing and testing the product managing project personnel and handling external organizations.

Are the managers experienced in software development software management the application domain the development process or on large projects 

Management Methods refers to methods for managing both the development of the product and project personnel.

Is there poor awareness of mission or goals poor communication of technical information among peers and managers 

Is there a non productive non creative atmosphere Do people feel that there is no recognition or reward for superior work 

Project Constraints is called Program Constraints in SEI 93 TR 6. The contractual organizational and operational factors within which the software is developed but which are generally outside of the direct control of the local management.

Resources address resources that the project is dependent on but are outside the project s control to obtain and maintain.

Project Interfaces deals with the various interfaces with entities and organizations outside the product development itself.

Are there any customer problems such as lengthy document approval cycle poor communication and inadequate domain expertise 

Are there any problems with associate contractors such as inadequately defined or unstable interfaces poor communication or lack of cooperation 

The Portfolio Health and Status Analysis provide a simple high level view of the performance data and indicate on track drifting or off track. Each project in the portfolio is shown and the ability to drill down to greater detail on each project allows managers and executives the ability to see the project at just the level they need to follow and manage the results.

The basis of the health and status analysis is a number of attributes for the execution of the project along with attributes for calculated performance limits. The various thresholds and limits are used to calculate and assign a heath status for the relevant measure. The status is to be displayed in a stoplight fashion green yellow and red for ok on track drifting and trouble respectively.

Financial data is tracked and displayed for each project with the ability to control time periods and organization units and roll ups. The data includes general expenses payroll and project revenue income.

The financials are displayable by business organizational unit with the ability to combine organizational units into a composite view. The organizational units to be combined are selectable by the user and selections persist across application sessions.

All financials must have the ability to be displayed at resolutions of weekly monthly quarterly and yearly with an optional ability to show the previous year against the current year with the same time resolution .

Key Goal Tracking allows an organization to list and conveniently report the current status of its key goals. A key goal is a quantifiable target of achievement that can be monitored and the status of meeting said goal can be displayed based upon data e.g. 25 Cost Reduction 99.2 SLA Met.

Each key goal has an assignable owner that is the person who is responsible for tracking and updating the status of the key goal.

There is a Key Goal maintenance page where Key Goals can be created edited and deleted. The Key Goal owner and administrators have the ability to update the health status of the goal using a stop light indicator green yellow and red as specified earlier for displaying of various health status indicators. From this maintenance page the owner and administrators will be able to define checkpoints along the course to satisfying the Key Goal which will include a deadline for each. Once created these checkpoints will exist under the Key Goal and can be checked off once they are completed. If the deadline on a checkpoint has passed without being completed the status of that Key Goal needs to be set to Red. Checkpoints can be added edited and removed at any time.

Objective Tracking allows an organization to list and conveniently report the current status of its objectives. An objective is unlike a Key Goal a non quantified target of achievement. While an objective may be monitored and tracked a status decision for an objective is based more upon the reporting manager s thoughts on progress than upon data e.g. SLA Improvements Increase Level 1 Helpdesk Resolution.

As with the Key Goals there is a maintenance page with a system to track tasks within each objective. Each objective has an assigned owner who is able to update the tasks within the objective. Each task within the objectives will have a description a deadline date and a check box to be checked once the task has been completed. If the deadline on a task has passed without being completed the status of that objective needs to be set to Red. Tasks can be added edited and removed at any time by the Objective owner or an administrator.

Multi level reporting allows varying details levels of the projects to be reported from easy to read stop light type charts to line and bar graphs to data sheets. These reports allow managers and executives to see appropriate detail levels for each project and area of interest.

Each user when logging in to the PMO will be presented with a view of the various analysis risk and data components that they have selected to see.

There is a standard view provided for users who have not customized their view. The standard view will show information about what would encompass the set of items that fall under that user s area of responsibility as defined by the authorizations given the particular user.

An IT manager will see a higher level summary of the projects that are under his control with the ability to drill down to the project level as desired.

Executive managers will see a summary of the entire portfolio with the ability to drill down to the project level as desired.

In addition to the standard reports and views the PMO must support ad hoc reporting using tools like e.g. Crystal Reports .

Using the MIT model of portfolio asset classification the balance of the portfolio across Infrastructure Transactional Informational and Strategic classifications is determined for tracking and comparison against the company s strategic focus.

The analysis uses a portfolio pyramid that is described by the following descriptions. At the base are the infrastructure investments. Built on that base are the transactional systems which need a reliable infrastructure . At the top are the information producing and strategic systems.

The PMO using the data gathered along with this model will analyze the investment distribution. This distribution is used to evaluate the orientation of the IT portfolio and determine the level of alignment with the company s strategic focus.

There needs to be the ability to Custom Define a new Portfolio Balance scheme as well as edit the Pre Packaged solution in case the original system does not fit the user s business or in case they already have a pre existing method to handle this data.

There needs to be a second Portfolio Balance Analysis system that will allow the balance of all current projects to be displayed based off the Business Area field in the Project Profile. This will allow the user to see the distribution of the Portfolio based on the business areas the projects are operating beneath.

This is a dynamically generated display method since the number of Business Areas varies between different users. Once viewing the distribution the user can select any of the Business Areas and be directed to a list of all the projects within the Business Area in the format described in the Portfolio Summary View detailed later in this document.

The Effort Distribution Analysis provides a manager with the ability to place a general effort breakdown of the project in the system for analysis and project plan validation. The effort breakdown is based on a table of percentages of total effort for each major phase in the lifecycle based on aggregate measures of completed projects. Such a table is tunable and verified by the application such that all roll ups come to the correct percentages and the total for the table rolls up to 100 .

Using the percentages listed in the table the system will determine if the projects breakdown is reasonable within a defined threshold for each phase. The indicators are a stop light view of each phase green yellow red to show where phases may be under or over estimated.

There is an updateable library of project templates including instructions and samples. The library is browsable by the user and allow viewing and downloading of the templates. Completed templates is uploadable to the system and assigned to associated with the particular project to which they pertain. The projects documents are viewable or downloadable by any appropriately authorized user.

There is a PMO homepage known as a Dashboard view which is the initial screen that users will see when they move into the PMO software. It is meant to give a quick informative overview of the data stored within the PMO. The Dashboard will need to display data such as but not limited to 

For any stop light indicator throughout the program that is determined via analysis of values a method must be created to display in which direction these items are varying from the baseline.

On the Dashboard main page if the mouse pointer hovers over one of the Projects a pop up appears to give an overview of the 6 project facet stop light indicators.

The Project Details screen is displayed when the user clicks on one of the links populating the Projects List.

All facets of the project are displayed with their corresponding stop light indicators. Each facet is listed as a link to its corresponding data display. Whichever graph or data form is being displayed at the current time is highlighted in this list in an obvious manner. Additionally the same highlighting is applied to which view the user is currently accessing.

There are always two sets of data displayed for the graphs the Actual and the Baseline. The yellow and red thresholds will also be graphed but these will be based upon a percentage or fixed value enumerated separately by the user. The graph will have a line for both Actual and Baseline as well as a variance line both above and below the baseline for the yellow and red thresholds.

The graph by default displays 26 weeks. This number is able to be changed within the program to show a user defined date range on a project by project basis. Weeks start on the Sunday of a given week.

The customer satisfaction and quality graphs do not utilize a baseline but rather definable target zones. The attributes associated with these graphs in addition to displaying the zones are the containment percent. The yellow and red lines will denote target zones.

The graph by default displays 26 weeks. This number can be changed within the program to show a user defined date range on a project by project basis. Weeks start on the Sunday of a given week.

Graphing is dynamic that is it includes a functionality that allows for the user to either define custom graphs or overlay existing graphs in order to analyze how changes in one graph influence others.

If data entry for the six project facets remains manual place all data entry for the facets on one page for quick entry of weekly data.

The data for the financial graph are input and stored in some fashion either automatically by working with Tracer or by manual input on the part of the project manager.

There is also a financial graph to display the cumulative totals over the period chosen by the administrator.

Database tables are created to hold required data for displaying the dashboard items. This will include the items being tracked as well as the detailed data for determining the status.

The system has data supplied weekly and be able to report on those data on a week by week basis. Each portfolio project will have an arbitrary number of weeks of baseline or planned data points one set for each week for each area. All project reporting areas will record weekly data point each area for use in comparing to the baseline or indicate the current health status .

This program is very graphic intensive with at least 6 graphs per project. In order to keep users navigating steadily through the data via any connection graphics size must be kept to a minimum.

 Portfolio Summary View will be is a separate page that the user can access from the main page. Perhaps have the icon located at the top of the Portfolio list next to the label Portfolio . That page will provide a general overview of basic facts regarding all of the projects inside the system. The projects will be sorted into one of two headings Active and Completed.

While a preferred embodiment of the invention has been described in detail above those skilled in the art who have reviewed the present disclosure will readily appreciate that other embodiments can be realized within the scope of the present invention. For example numerical values are illustrative rather than limiting as are recitations of specific hardware software and programming techniques. Also the features of the invention can be implemented in a different order from that disclosed herein. Therefore the present invention should be construed as limited only by the appended claims.

