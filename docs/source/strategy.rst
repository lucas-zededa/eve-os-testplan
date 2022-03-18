Testing Strategy
================

In order to make the process of developing EVE and making its functionality
testable, we need to reduce the friction necessary to run automated tests,
as that is the only reasonable way we can do comprehensive, repeatable and
reliable testing.

Functional
----------

Functional testing verifies the software functionality against specifications.

For EVE OS, we currently have the following aspects covered:

Eden default test - github
**************************

https://github.com/lf-edge/eden/actions/workflows/eden.yml

Eden GCP test - github + gcp machine
************************************

Test new version of Eden with Eve version specified in eden. Tests both KVM/XEN backends.

https://github.com/lf-edge/eden/actions/workflows/eden_gcp.yml

Eden setup - Checks that eve image is generated
***********************************************

https://github.com/lf-edge/eden/actions/workflows/eden_setup.yml

Eden default test - Github
**************************

https://github.com/lf-edge/eve/actions/workflows/eden.yml

Eve GCP test - github + gcp machine
***********************************

Test new version of Eve with current Eden version. Tests both KVM/XEN backends.

https://github.com/lf-edge/eve/actions/workflows/eden_gcp.yml

Integration
-----------

Integration testing aims to evaluate the SUT against project dependencies,
often targeting real world user scenarios. For EVE OS we cover the following aspects:

* Application Deployment
    * Create a Project
    * Create a Data Store
        * AWS
        * Azure Blob
        * Local HTTP
        * SFTP
        * Docker Container registry
    * Create an image
        * Create a QCOW2 image
        * Create an OVA image
    * Create a Network Instance
        * Create a Local DHCP network instance
        * Create a Local Static network instance
        * Create a Switch network instance
        * Create an Internal network instance
    * Create Application Bundles (VM)
        * Create application bundles
    * Create Application Bundles (Container)
        * Create container application bundles
    * Create two Application Instances (VM)
        * Create application instances (VM)
    * Create two Application Instances (Container)
        * Create application instances (Container)
    * Device Management
    * IP assignment using DHCP
        * Static IP configuration to Interfaces
        * Configure a Direct Attach Interface
        * Configure an interface as App shared with a NAT network interface
        * Configure an interface as App shared with a switch networkinterface
        * Configure Port mapping
        * Verify ACLs
        * Configure Proxy into a network
        * Test Inter-VM communication
        * Test Inter-Container communication
        * Test VM-Container communication
    * Administration, Access Control and Security
        * Add user with SysAdmin role
        * Add user with SysOperator role
        * Add user with SysMonitor role
        * RBAC - Admin
        * RBAC - SysManager
        * RBAC - SysMonitor
        * RBAC - SysOperator
        * TPM and data encryption
    * Health monitoring
        * CPU Utilization of app and device
        * Memory utilization of app and device
        * Storage utilization of app and device
        * Network counters for app instance and device
        * Verify Status of app instance and device
        * Verify Events of app instance and device
        * Verify Traffic and top talkers
* After Cloud upgrade
    * On Dev_Upgrade device
    * Application Lifecycle
        * Deactivate Application instance
        * Activate Application instance
        * Restart Application instance
        * Edit resources in app bundle and update the app instance
        * Edit resources in app bundle and force update the app instance
        * Edit the ACLs and update the app instance, verify the ACLs
        * Test Inter-VM communication
        * Test Inter-Container communication
        * Test VM-Container communication
    * Health monitoring
        * CPU Utilization of application instance
        * Memory utilization of application instance
        * Storage utilization of application instance
        * Network counters for application instance
* After Device (EVE / base OS) upgrade
    * Application Lifecycle
        * Delete Applications
        * Create and activate applications again (VMs and Containers)
        * Deactivate Application instance
        * Activate Application instance
        * Restart Application instance
        * Purge andRestart Application instance
        * Replace the image in app bundle and update the app instance
        * Edit resources in app bundle and force update the app instance
        * Edit the ACLs and update the app instance, verify the ACLs
        * Test Inter-VM communication
        * Test Inter-Container communication
        * Test VM-Container communication
    * Health monitoring
        * CPU Utilization of application instance
        * Memory utilization of application instance
        * Storage utilization of application instance
        * Network counters for application instance

Performance
-----------

Performance testing checks how a system behaves in terms of their main performance
metrics. The performance metrics include speed (time it takes for the application
to perform a significant computational test), scalability (maximum user load the
application can handle) and latency (time between requesting data from the application
and data reaching the requester). The idea is to keep track of historical data
to identify, prevent or fix regressions.

`Performance test scenarios <https://github.com/lf-edge/eden/blob/master/docs/io-performance-tests.md>`_

`Performance test <https://github.com/lf-edge/eden/tree/master/tests/io_performance>`_

Load/Stress
-----------

Tests aimed to verify the application's ability to perform under anticipated user loads.
The idea is to identify performance bottlenecks prior to release. Current state is TBD.

Security Testing
----------------

Security testing is the selective retesting of a system or component to verify
that modifications have not caused unintended security vulnerabilities and
compromise the product. Current state is TBD.
