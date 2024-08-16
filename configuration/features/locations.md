---
description: >-
  This documentation will guide you through how locations are used in OpenMRS 3
  and how to configure them via the Admin UI or the Initializer module.
---

# Locations

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-16 at 9.47.37 AM (1).png" alt=""><figcaption></figcaption></figure>

</div>

## Configuration Guide

OpenMRS 3 uses **Locations** to define the places where clinical care, administrative work, and other activities are conducted within the system. These locations can represent physical spaces (e.g., clinics, wards, pharmacies) or logical spaces (e.g., departments or service areas). Proper configuration of locations is crucial for ensuring that patient records, workflows, and other system functionalities are accurately mapped to the right places.



### Table of Contents

1. Overview of Locations in OpenMRS 3
2. Configuring Locations via Admin UI
3. Configuring Locations via the Initializer Module
4. Best Practices for Location Configuration

### Overview of Locations in OpenMRS 3

#### Purpose of Locations

Locations in OpenMRS serve several key functions:

* **Visit Management**: Encounters, visits, and admissions are tagged with the location where they occur.
* **Data Segmentation**: Clinical data, such as observations and orders, can be filtered or organized by location.
* **Role-Based Access**: Access to specific parts of the system can be restricted or configured based on location.
* **Service Routing**: Certain services (e.g., laboratory, radiology) may be tied to specific locations within the system.

#### Types of Locations

* **Physical Locations**: e.g., hospital wards, clinics, pharmacies, laboratories.
* **Logical Locations**: e.g., departments, administrative units, or services that are not tied to a specific physical space.

In OpenMRS 3, locations are hierarchical, meaning that you can create parent-child relationships between locations (e.g., a hospital contains multiple departments, each with wards).

### Configuring Locations via Admin UI

The Admin UI provides a user-friendly interface to create and manage locations in OpenMRS 3.

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-16 at 9.55.27 AM.png" alt=""><figcaption></figcaption></figure>

</div>

#### Steps to Configure Locations via Admin UI

1. **Access the Admin UI:**
   * Log in to your OpenMRS instance.
   * Navigate to the **System Administration** section.
   * Click on **Manage Locations**.
2. **Create a New Location:**
   * Click the **Add Location** button.
   * Fill in the required fields, including:
     * **Name**: The name of the location (e.g., "General Ward").
     * **Description**: A brief description of the location’s purpose.
     * **Parent Location**: If this location is part of a hierarchy, select the parent location.
     * **Tags**: You can optionally assign tags to help categorize and filter locations.
   * Click **Save** to create the location.
3. **Edit an Existing Location:**
   * From the **Manage Locations** page, click the **Edit** icon next to the location you wish to modify.
   * Update the location details as needed and click **Save**.
4. **Remove a Location:**
   * To remove a location, click the **Delete** icon next to the location. Note that locations tied to existing data (e.g., encounters) cannot be deleted without first reassigning or removing those associations.

#### Location Attributes

* You can also configure custom attributes for locations through the Admin UI. For instance, you might want to track details like room capacity or facility type. These attributes can be added by clicking on **Manage Location Attributes** under the System Administration section.

### Configuring Locations via the Initializer Module

The Initializer module provides a powerful way to configure locations using configuration files. This method is particularly useful for automating deployments or setting up locations programmatically.

<div data-full-width="true">

<figure><img src="../../.gitbook/assets/Screenshot 2024-08-16 at 10.07.17 AM.png" alt=""><figcaption></figcaption></figure>

</div>

#### Steps to Configure Locations via the Initializer Module

1. **Install the Initializer Module:**
   * Ensure that the Initializer module is installed and running in your OpenMRS instance.
2.  **Prepare the Configuration File:**

    * Create a CSV file that defines your locations. The file should include the following columns:
      * **Name**: The name of the location.
      * **Description**: A brief description of the location.
      * **Parent Location**: (Optional) The name of the parent location, if applicable.
      * **Tags**: (Optional) Tags for categorization.
      * **UUID**: (Optional) The unique identifier for the location (used for updates).

    Example CSV content:

    ```csv
    name,description,parentLocation,tags,uuid
    General Ward,Main ward for general patients,Hospitals,WARD,uuid-of-general-ward
    Outpatient Clinic,Clinic for outpatients,Hospitals,CLINIC,uuid-of-outpatient-clinic
    ```
3. **Upload the Configuration File:**
   * Place the CSV file in the appropriate directory within the Initializer module’s configuration folder, typically found under `configuration/domain/locations`.
   * The Initializer module will automatically process the configuration file and create or update the locations upon the next startup or manual trigger of the module.
4. **Verify the Configuration:**
   * Once the configuration has been applied, log in to OpenMRS and navigate to the **Manage Locations** page to verify that your locations were created successfully.

### Best Practices for Location Configuration

* **Plan Your Hierarchy**: Before creating locations, plan out the structure. Start by defining higher-level locations (e.g., hospitals or departments) and then create more granular locations (e.g., wards, rooms).
* **Use Descriptive Names**: Make sure your location names are clear and descriptive, so they are easily recognizable to users.
* **Tag Your Locations**: Use tags to help categorize and filter locations in reports and workflows.
* **Automate with Initializer**: If managing multiple locations or deploying across multiple instances, use the Initializer module to automate configuration and reduce the risk of human error.

### Conclusion

Configuring locations in OpenMRS 3 is a critical step to ensuring that your system accurately reflects the physical and logical structure of your organization. By using the Admin UI for manual configuration or the Initializer module for automation, you can effectively manage locations to support patient care and administrative workflows.

For more information on locations and other configurations, refer to the [OpenMRS Wiki](https://wiki.openmrs.org/).
