# Admin Portal User Guide

## Overview
To get started with using the Admin portal, an admin user must be assigned to a zone.

## Creation of first Admin user
1. Setup of hierarchial zones 
2. Create Admin roles in KeyCloak
3. Create first admin user in KeyCloak
4. Assign first user to root zone 

The above are done automatically as part of [default sandbox installation](https://github.com/mosip/mosip-infra/tree/1.2.0-rc2/deployment/v3).

## First user login

![](_images/admin-login.png)
 
1. Select the preferred language. 
2. Login with KeyCloak credentials.

![](_images/admin-home.png)
 
## First user actions
1. Map the other users(admins/registration operators/supervisors) to respective zones
2. Create centers and assign the users to a particular center
3. _Highly recommended_: Ensure to revoke the first super user's zone mapping and role after first user actions are completed.

## Admin roles and their default accessibility matrix
*  GLOBAL_ADMIN
*  ZONAL_ADMIN
*  REGISTRATION_ADMIN
*  MASTERDATA_ADMIN
*  KEY_MAKER

|GLOBAL_ADMIN|ZONAL_ADMIN|REGISTRATION_ADMIN|MASTERDATA_ADMIN|KEY_MAKER|
|------|-----|-----|-----|-----|
|Centers|Devices|Packet Status|All Master Data|GenerateMasterKey|
|User Zone Mapping|Machines|Pause/ Resume RID|Bulk Upload||||||
|All Master Data|User Zone Mapping|Retrieve Lost RID|GenerateCSR|||||
|Bulk Upload|User Center Mapping|Packet Upload|GetCertificate||||
|GenerateCSR|All Master Data||UploadCertificate|||
|GetCertificate|Bulk Upload||UploadOtherDomainCertificate||
|UploadCertificate|GenerateCSR||||
|UploadOtherDomainCertificate|UploadCertificate||||
||UploadOtherDomainCertificate||||

## Resources 
The various resources that can be managed by an Admin are:
1. Center (registration centers)
1. Device
1. Machine
1. Users (Admin, registration staff) 

## Center 

* This portal allows an Admin to view, create, edit, activate, deactivate and decommission registration centers.
* An Admin can manage only centers under his/her [administrative zones](administration.md#administrative-zones).

![](_images/admin-view-center.png)

The administrator can filter the list of registration centers based on parameters like *Center name, Center type, Status, Location code*.
 
![](_images/admin-view-center-filter.png)

* The system does not fetch the details of decommissioned registration centers but only active and inactive centers are displayed. 
* If the admin does not find a center, they can click the *Center not available in logged in language* button. Clicking on this button, displays the list of centers that are already created in other languages. On selecting a particular center, the information will be auto-populated in the Create page and be made available to the admin for modifications.
* Language specific fields can be modified to create a center with the currently logged in language.

### Create center

![](_images/admin-create-center.png)

* A center is created with multiple attributes and is mapped to the administrative zone that it belongs to.
* A center can only be mapped to the configured location hierarchy level. 
* While defining centers, an admin can also define the working days of the week for a center and any exceptional holidays that might be applicable for a particular center.

### Update Center

![](_images/admin-edit-center.png)

* An admin can update a center once a center is created. The updates can include adding the details that were missed during creation of the center or changing the details of a center as required.
* To update, click the **Edit** option from the Actions menu against a center name.

*Note - Updates made to language specific fields updates data only for that language in the database while updates made to non-language dependent fields updates data against all the language entries for that center*. 

### Activate/deactivate/decommission center

![](_images/admin-deactivate-center.png)

* Select the **Deactivate/Decommission** option from the Actions menu against the center.
* Activation/Deactivation/Decommission of a center in one language will be applied to the same center created in all the languages.

To know more, refer [Activate/deactivate/decommission resources](administration.md#Activate/deactivate/decommission-resources)

## Devices

**Note: Device entity is language agnostic.**

* Admin Portal allows an administrator to manage the Devices a country will use for registering residents like devices used for bio-metric capture (Fingerprint, Iris, Web camera, etc.), printers, scanners.
* Device management includes Viewing, Creating, Editing, Activating, Deactivating and Decommissioning of Devices.
* The Admin portal allows an administrator to view the list of all Devices available in the jurisdiction of their administrative zone. 
* The system does not fetch the details of Decommissioned Devices but only Active and Inactive Devices. 

![](_images/admin-view-device.png)

The Admin can filter the list of Registration Centers based on parameters like *Device Name, Mac Address, Serial Number, Status, Map Status, Device Type, Device Spec ID.

![](_images/admin-view-device-filter.png)

**Create Devices**

![](_images/admin-create-device.png)

A Device can be created with the multiple attributes and be mapped to the Administrative Zone it belongs to. 

**Update Devices**

![](_images/admin-edit-device.png)

* An admin can update missing information or change device details even after it is created.
* To update, click the **Edit** option from the Actions menu against a device.

**Activate/Deactivate/Decommission Device**

![](_images/admin-deactivate-device.png)

To Activate/Deactivate/Decommission Device, select the **Deactivate/Decommission** option from the Actions menu against the device.

**Map/Un-map/Re-map Device to a Center**

![](_images/admin-map-device-center.png)

* Admin portal allows an Admin to map/un-map each Device to a Center.
* This mapping specifies as to which Center the Device will be used in.
* A Device can only be mapped to a Center which belongs under the Device’s Administrative Zone.
* To do so, select the device and choose a **Center Name** from the dropdowm.

## Machines
* Admin portal allows an administrator to manage the machines a country will use for registering residents. 
* In MOSIP, a machine is a device on which the registration client is installed.
* Machine management includes viewing, creating, editing, activating, deactivating and decommissioning of machines. 
* The admin portal allows an admin to view the list of all the machines available in the jurisdiction of his/her administrative zone. 
* While viewing, the system does not fetch the details of decommissioned machines but only shows the active and inactive machines. 

![](_images/admin-view-machine.png)

The administrator can filter the list of machines based on parameters like *Machine name, Mac address, Serial number, Status, Machine type.*

![](_images/admin-view-machine-filter.png)

 **Create Machines**
![](_images/admin-create-machine.png)

* A Machine can be created with the attributes like *Machine ID, machine name, mac address, serial number, machine spec ID and administrative zone* the machine belongs to.
* While entering data through UI in multiple languages, the dropdown values and numeric values entered in primary language gets automatically captured in all language.
* But the text fields (e.g., machine name) needs to be manually input in all the languages. A machine can be mapped to the administrative zone which is at the any zonal hierarchy.

**Update Machines**

![](_images/admin-edit-machine.png)

* An admin can update missing details or make changes to machine details even after it is created. 
* To update, click the **Edit** option from the Actions menu against a machine.

*Note - Updates made to language specific fields updates data only for that language in the database while updates made to non-language dependent fileds updates data against all the language entries for that center.* 

**Activate/Deactivate/Decommission Machine**

![](_images/admin-deactivate-machine.png)

An admin can deactivate or decommission a machine through the admin portal.

**Map/Un-map/Re-map Machine to a Center**

* Admin portal allows an Admin to map/un-map each Machine to a Center. This mapping specifies as to which Center the Machine will be used in.
* A Machine can only be mapped to a Center which belongs under the Machine’s Administrative Zone.
* To do so, select the machine and choose a **Center Name** from the dropdowm.

## Users

* MOSIP uses Keycloak as an IAM (Identity access management tool) for managing Users. These users are internal users of MOSIP including Registration Officers, Registration Supervisors, Zonal Admins, Global Admins etc.
* User Management includes Viewing, Creating, Editing, Activating, Deactivating and Blacklisting of Users.

### User Zone Mapping

![](_images/admin-user-zone-list.png)

Once the user is created in KeyCloak, they need to be mapped to a zone to get access to specific information available in that zone.

**Map/Un-map/re-map user to a Zone**

![](_images/admin-user-zone-map.png)

To map a user to a zone,
1. Click Resources-> User Zone mapping
2. Click **+Map Zone**
3. Select the *User Name, Administrative Zone* from the dropdown.
4. Click **Save**.

To re-map a user to a zone,
1. Click Resources-> User Zone mapping
2. Select **Remap** from the Actions menu against the mapped user.
3. Update the *User Name/ Administrative Zone* from the dropdown.
4. Click **Save**.

Note: If the center is mapped already, the admin needs to unmap the center to remap the zone.

* Admin portal allows an admin to map users to a zone. This mapping specifies as to which zone the user will belong to.
* A user can only be mapped to a zone which belongs under the user’s Administrative Zone.
* A user can later be un-mapped from the zone in case a user needs to be moved to another zone. In such cases, the user will later need to be mapped to the new zone. 

![](_images/admin-user-zone-mapping.png)

### User Center Mapping

![](_images/admin-user-center-list.png)

* Once the user is mapped to a zone, they will be listed in the screen below. Now, the user will be mapped to a center to be able to manage their assigned center.
* Admin portal allows an admin to map users to a center. This mapping specifies as to which center the user will be used in. 
* A user can only be mapped to a center which belongs under the user’s Administrative Zone.
* A user can later be un-mapped from the Center in cases where a User is needed to be moved to another Center. In such cases, the user will later need to be mapped to the new center. In case the user is required to be mapped to a Registration Center outside the Administrative Zonal restriction, the Administrative Zone of the user must be changed.

**Map/Un-map/re-map user to a Registration Center**

![](_images/admin-user-center-map.png)

To map a user to a center,
1. Click Resources-> User Center Mapping
2. Select **Map** from the Actions menu against the mapped user.
3. Select the *Center name* from the dropdown against the User Name, Administrative Zone.
4. Click **Save**.

## Packet status (based on RID)
* A Registration packet generated in Registration client is sent to Registration Processor for further processing and UIN generation. 
* Using this Portal, A Registration Admin can view the status of a packet by entering the RID of the packet. 
* The packet status will contain all the stages the packet has passed through along with the last stage the packet is in. 
* In case the packet has not been processed or is marked for *Re-Send/Re-Register*, the admin will be able to view specific comments indicating the reason for that particular status.

![](_images/admin-packet-status.png)

## Pause/Resume RID 
* The Registration Admin has the privilege to view the registration packets that are in a paused state.
* Admin can use this portal to resume or reject paused packets. They would have 3 options:
    * Resume processing (from where it was paused)
    * Resume from the beginning 
    * Reject 

Once processing of a packet is resumed, it will be removed from this list

## Retrieve lost RID
* The Registration Admin can use this feature to retrieve lost RID.
* For instance, if the resident did not provide any valid email and/or phone number and has lost the RID slip received during the registration, in order to find their RID details, the resident contact MOSIP helpline and share details such as name, centre name, registration date and postal code to the admin, who will use the lost RID feature and try to retrieve the RID number.

A few filters may be applied to retrieve the RID.

![](_images/admin-retrieve-lost-rid.png)

Note: This feature is currently under development.

## Master Data
* Admin portal allows an Admin to manage the Masterdata applicable for a country.
* These data includes list of Genders, list of Holidays, Templates, Center Types, Machine Types etc. This data is used by all the modules across MOSIP which includes Pre-Registration, Registration Client, Registration processor and ID-Authentication.

![](_images/admin-master-data.png)

To know more, refer to Master Data guide.

## Bulk upload

![](_images/admin-list-bulk-upload.png)

* If a country decides to insert the data through the .csv files, they could use this feature to upload the existing data into the MOSIP platform.
* The listing screen displays the uploaded data transaction information. 
* As the information inside .csv files may be huge, it would go through the batch job to process the information and store it in the tables. Also, it may take time to get  unique transaction ID against the particular action.

**Master Data**

![](_images/admin-upload-masterdata.png)

 To upload Master data using Admin portal,
 1. Go to Bulk Upload > Master Data
 2. On the master data dashboard, click **Upload Data**.
 3. Select the operation (insert/update/delete)
 4. Select the table name into which the data needs to be uploaded into.
 5. Click **Choose file** to select the data and click **Upload**
 
To view the format for inserting data in a particular table, click on the Download icon. A CSV file gets downloaded in which the first row represents the column names and the rest of the rows are the data which will be inserted into the table(sample).

**Packets**

 ![](_images/admin-packet-bulkupload.png)

 To upload packets using Admin portal,
 1. Go to Bulk Upload > Packets 
 2. On the packet upload dashboard, click **Upload Packet**.
 3. Select the following from the dropdown:
     * Center name
     * Source (currently displays Registration Client)
     * Process (New, Update UIN, Lost, Biometric correction)
     * Supervisor status (Approved/Rejected)
 4. Click **Choose file** to select the packets and click **Upload**.
 
*For uploading the packets through the Admin portal, ensure that the packets are available in the machine or the external hard disk connected from where the Admin Portal is being used.*

## KeyManager (taheer)
* The admin user can manage the key using this feature.

**GenerateMasterKey**

![](_images/admin-generate-masterkey.png)

**GenerateCSR**

![](_images/admin-generate-csr.png)

**GetCertificate**

![](_images/admin-get-certificate.png)

**UploadCertificate**

![](_images/admin-upload-certificate.png)

**UploadOtherDomainCertificate**

![](_images/admin-upload-anotherdomain-certificate.png)


