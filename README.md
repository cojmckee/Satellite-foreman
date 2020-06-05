Satellite
=========

Satellite role is a ansible role to install and configure Red Hat Satellite 6.5

Requirements
------------
System Requirements
- x86_64 architecture
- The latest version of Red Hat Enterprise Linux 7 Server
- 4-core 2.0 GHz CPU at a minimum
- A minimum of 20 GB memory is required for Satellite Server to function. In addition, a minimum of 4 GB  of swap space is also recommended. Satellite running with less memory than the minimum value might not operate correctly.
- A unique host name, which can contain lower-case letters, numbers, dots (.) and hyphens (-)
- A current Red Hat Satellite subscription
- Administrative user (root) access
- A system umask of 0022
- Full forward and reverse DNS resolution using a fully-qualified domain name

Storage Requirements
- 2 Storage devices
- 73 Gib Storage devices for OS
- 600 Gib Storage device for Satellite (Connected/Disconnected)
- 1200 Gib Storage device for Satellite (Master)

Role Variables
--------------
1. Red Hat Satellite version that is going to be installed
   - satellite_deployment_version: 6.5
2. User that has permission to register to Red Hat Network
   - RHN_USER= (access.redhat.com account)
3. User Password for the account
   - RHN_PASSWORD = (access.redhat.com account password )
4. Account ID from Red Hat Entitlments
   - SAT_ACCOUNT_ID = CHANGEME
5. Red Hat Network Activation key
   - RHN_AK= CHANGEME-AK
6. Your Organization ID in Red Hat Network
   - RHN_ORG= CHANGEME
7. Intial Admin username that will be configured during install
   - FOREMAN_USER=admin
8. Intial admin passowrd that will be configured during install
   - FOREMAN_PASSWORD= somepassword
9. Intial Organization nmae that will be configured during install
- FOREMAN_INITIAL_ORGANIZATION = SOMEORG
10. Intial location that will be configured during instal
- FOREMAN_INITIAL_LOCATION= SOMELOCATION
11. Location of the satellite manifest
    - SATELLITE_MANIFEST= SOME_PATH_TO_MANIFESTexport RHN_USER='levelup_redhat'
12. Set if satellite is disconected, connected
    options disconnect, connect, or master
    - RHN_CONNECT='changeme'  
13. This is needed for a disconnected satellite install
    - CONTENT_SOURCE='https://fqdn/pub/iss/'
14. Location where the manifest location
    - SATELLITE_MANIFEST='filesystem path to the manifest.zip is'
15. Account id from the manifest
    - SAT_ACCOUNT_ID='00000000'


Dependencies
------------
Create satellite manifest from access.redhat.com before hand, currently stored on the gitlab runner, but will be stored on an s3 bucket.
The manifest must be updated manually until we get the api for access working.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: satellite }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
