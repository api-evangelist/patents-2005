---

title: Quiescence mode for a portal
abstract: A quiescence mode for a portal allows a portal configuration to be protected from changes. This allows the configuration to be maintained during long running operations without a risk that the portal configuration will be changed during the operation.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07607139&OS=07607139&RS=07607139
owner: BEA Systems, Inc.
number: 07607139
owner_city: Redwood Shores
owner_country: US
publication_date: 20050418
---
This application claims priority to U.S. Provisional Application No. 60 573 308 entitled Quiescence Mode by Laird et al. filed May 21 2004.

Portals can provide access to information networks and or sets of services through the World Wide Web and other computer networks. Portals can provide a single point of access to data and applications making them valuable to developers businesses and consumers alike. A portal can present a unified and personalized view of enterprise information to employees customers and business partners. In many implementations portal applications can include web application views designed as a portal.

Portals are capable of presenting multiple web application views within a single web interface. In addition to regular web content that can appear in a portal portals provide the ability to display portlets self contained applications or content in a single web interface. Portals can also support multiple pages with menu based or custom navigation for accessing the individualized content and portlets for each page.

A working portal can be defined by a portal configuration. The portal configuration can include a portal definition such as a file including Extensible Markup Language XML portlet definition files for any portlets associated with the portal java server pages JSPs web application descriptors images such as graphics interchange format files GIFs deployment descriptors configuration files the java archive files JAR that contain the logic and formatting instructions for the portal application and any other files necessary for the desired portal application.

Portals are powerful Web sites can give users a single point of access to applications and information in a unified interface. A portal lets users view each application in its own window called a portlet and a single browser window can contain multiple portlets.

Portals can provide access to information networks and or sets of services through the World Wide Web or other computer networks. These networks can range from broad interconnections of computing systems such as the Internet to localized area networks including a few computers located in close geographic proximity such as a home or office. Portal applications can include web application views designed as a portal.

Portlets can be implemented as java server pages JSPs referenced by XML based metadata of the portal descriptor. Portlets can utilize various types of display code to display highly focused information directed to a specific user or user group having a portal as its container. Portlets can be comprised of portlet components which include portlet attributes i.e. whether the portlet is editable floatable minimizable maximizable helpable mandatory has defaults minimized or whether login is required and portlet layout elements or components i.e. banner header content and footer sections .

In one embodiment the quiescence mode is helpful for periods when changes to the portal configuration could interfere with another operation. For example the quiescence mode is valuable during a configuration backup or during application propagation such as when a live environment is updated with changes from a test environment.

In one embodiment the quiescence mode includes multiple modes. The quiescence mode can include a read only mode where the portal can be produced from the portal configuration but the portal configuration cannot be changed. The quiescence mode can include a static mode in which the portal application is not accessible. Other modes can include a prepare mode that warns a user not to change the portal configuration. In an inactive mode the portal configuration can be changed in the normal manner.

In one embodiment an object stores the quiescence mode information. The object can be an MBean which insures that all servers of a cluster get the quiescence mode information from the object. The JAVA Management Extension JMX specification and the JMX Application Programming Interface API model system and administration functions with MBeans. MBeans used to manage an enterprise application can include administration configuration and runtime MBeans. Administration MBeans contain a set of attributes that define configuration parameters for management functions. In one embodiment a configuration file such as config.xml is located at a machine hosting an administration server which provides persistent storage of MBean attribute values. Whenever an attribute is changed using an administration console administration tool or visitor tool the values can be stored in the appropriate administration MBean and written to the config.xml file. Configuration MBeans are copies of the administration MBeans that the other servers use to initialize their configuration. Runtime MBeans are attributes consisting of runtime information for active application servers and instances in applications.

In one embodiment APIs are used to access the object storing the quiescence mode information. A read API can be used to read the quiescence mode information from the object. A write API can be used to write the quiescence mode information to the object. The object can be checked before changing the portal configuration.

Delegated administration can be used to ensure compliance with the quiescence mode. Delegated Administration is a system that can restrict the access to data through an admin tool of a portal product to administrators and those designated by the administrators. Delegated administration information indicates what portal elements are accessible by what users. The delegated administration can be expanded to check for the quiescence mode information using quiescence mode APIs. Other systems such as locking or entitlements can also be expanded to implement the quiescence mode.

The administration tools or visitor tools for the portal can be used to set the quiescence mode information. The quiescence mode APIs can be accessed using a quiescence mode portlet.

A propagation tool can be used to automatically set the quiescence mode information. A propagation tool can be used for transferring changes made in a test environment to a live environment. The propagation tool can call the quiescence mode service to lock out changes to an environment while the update is taking place since large updates can take a significant amount of time.

In one embodiment stored quiescence mode information is used to determine whether to display a portal element of the portal for making changes to stored information. When the quiescence mode is set the changes to the stored information are prevented for all users.

The portal element can be part of an administration tool and the stored information can be a portal configuration. In this case the user is prevented from making changes to the portal since the administration tool page does not allow changes.

In one embodiment the portal element is part of a user portal page. The quiescence mode can then be used as a service so that a portal can prevent changes to data other than the portal configuration though the lack of display of a portal element.

The quiescence mode can provide a means to prevent the display or update of stored information by more than one system at the same time. In one example the display of the update configuration portlet is prevented so that we can update the configuration information via other means without having conflicts between the two sets of changes. In this case we would use a propagation tool to move data from staging to production and know the update configuration portlet cannot interfere with this process thus maintaining integrity of the configuration data.

Staging environments are used for large enterprises. Migration of portal data from staging to production is critical. In one embodiment a propagation tool can be used. In step a production environment is frozen with the quiescence service. In step the staging environment and production environment are compared. In step the propagation tool creates a propagation plan. In step the propagation plan is followed to update the production environment. The propagation tool can move content selectors property sets users groups entitlements desktops pages books portlets and other info from the staging environment to the production environment.

The quiescence service is extensible for customer authored applications to block changes to their data. One example would be an order entry system there might be a time during upgrades when you want to block order entry into a database but still allow the system to display previously entered orders. Application data such as customers orders can also suffer from problems if it is changed during migration from staging to production or during upgrades. The quiescence service can provide a locking mechanism for any type of data be it configuration data or application data.

Looking again at in one embodiment the constructed portal is implemented on a server . The server can implement the JAVA 2 Platform Enterprise Edition J2EE available from Sun Microsystems Inc. of Santa Clara Calif. For example the server can be a WebLogic Server available from BEA Systems Inc. of San Jose Calif.

Portal product can be used to create and administer portals. A portal designer can provide for the creation of the portal configuration. The portal configuration defines the portal and can be used to construct portal views. The portal product can be WebLogic Portal available from BEA Systems Inc. of San Jose Calif.

Administration tools can be used for administering a portal. Portal administration involves tasks that control the behavior content and appearance of portals. While portal administrators do not develop the resources required for a portal Web site they use those resources to maintain and modify portals. Administration tasks include setting up and managing users creating and managing group portals modifying portal attributes creating personalization behavior developing campaigns and changing a portal s look and feel. The administration tools can use delegated administration to prevent unauthorized users from accessing certain portal resources.

Administration tools can be used to create modified database based portals. In one embodiment a portal file is obtained by the administration tool modifications can be made for a user or group of users and the modified portal description can be stored as portal XML in a database.

A client can access the portal across a network by using a portal Uniform Resource Locator URL . The portal description and components are used to construct the portal for the client.

Visitor tools can allow users or sub administrators to modify the portals similar to the administrative portal. The administrative tools can be used to select what elements of the portal can be modified by the user or sub administrator through the visitor tools . The user or sub administrator can then set up the portal to their liking within the limits set by the administrator.

This section discusses one embodiment of the mode will be toggled persisted and read. The Portal Admin Tools can use MBeans to track the quiescence mode. The mbean can track several pieces of data 

The API can be supported by a single interface for both read and write operations. The implementation of the service can be application scoped which will eliminate the need for callers to pass the application name through the interface.

If the user has the privilege changes the QM mode of the cluster immediately. Also records the reason in the audit trail.

If the user has the privilege removes the mode from the QM mode list. Will not allow the removal of the default modes.

A number of modes can be available to the administrator. Each mode can vary in both severity and scope. Severity is defined by the types of operations that are restricted reads updates creates deletes and scope is defined by the components affected by the mode CM Portal Framework Campaigns etc .

A natural progression from the severity and scooping requirement is to define a set of capabilities and a set of resources. The capabilities map to the severity aspect and the resources map to the scope aspect. Although QM could define such a structure it begins to look like a problem that has already been solved by WLP.

A portlet can be provided for the Portal Admin Tools to change the current quiescence mode. A command can be added to a Scripting environment to change the QM mode. The setting of the QM mode can be an authorized operation. This operation will be protected using DA at the API level.

One embodiment may be implemented using a conventional general purpose or a specialized digital computer or microprocessor s programmed according to the teachings of the present disclosure as will be apparent to those skilled in the computer art. Appropriate software coding can readily be prepared by skilled programmers based on the teachings of the present disclosure as will be apparent to those skilled in the software art. The invention may also be implemented by the preparation of integrated circuits or by interconnecting an appropriate network of conventional component circuits as will be readily apparent to those skilled in the art.

One embodiment includes a computer program product which is a storage medium media having instructions stored thereon in which can be used to program a computer to perform any of the features presented herein. The storage medium can include but is not limited to any type of disk including floppy disks optical discs DVD CD ROMs micro drive and magneto optical disks ROMs Rams EPROM s EPROM s Drams Rams flash memory devices magnetic or optical cards Nan systems including molecular memory ICs or any type of media or device suitable for storing instructions and or data.

Stored on any one of the computer readable medium media the present invention includes software for controlling both the hardware of the general purpose specialized computer or microprocessor and for enabling the computer or microprocessor to interact with a human user or other mechanism utilizing the results of the present invention. Such software may include but is not limited to device drivers operating systems execution environments containers and user applications.

The foregoing description of preferred embodiments of the present invention has been provided for the purposes of illustration and description. It is not intended to be exhaustive or to limit the invention to the precise forms disclosed. Many modifications and variations will be apparent to one of ordinary skill in the relevant arts. For example steps performed in the embodiments of the invention disclosed can be performed in alternate orders certain steps can be omitted and additional steps can be added. The embodiments were chosen and described in order to best explain the principles of the invention and its practical application thereby enabling others skilled in the art to understand the invention for various embodiments and with various modifications that are suited to the particular use contemplated. It is intended that the scope of the invention be defined by the claims and their equivalents.

