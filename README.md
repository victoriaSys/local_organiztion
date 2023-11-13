Local Organiztion Plugin
=============================

Prerequisites
-------------
1. This plugin uses `local_sysbindapi`, `tool_sisync`, `webservice_restful`(Notice: the version that was devloped by Frédéric Massart <fred@branchup.tech>)
2. Should be enabled:
    - `web services`
    - `protocols: rest,restful`
3. Configure SiS Synchronizer settings (including mapping the mdl_tool_sisync_map table)
4. Configure Local Organization settings
5. Create mapping services for: courses, groups, categories
6. Make sure you have 'hujiid' field as user custom field

Creating users from Rama DB
----
After we configured the `tool_sisync` settings, 
we use the prepared DB to create users in moodle. 
 - Running the scheduled task 'Synchronizer Sync full Task' when first creating all users.
 - To update users(if data changed in Rama DB, only if 'renew' field = 1) - we run the scheduled task: 'Synchronizer Sync Diff Task'



Usage
-----
Running the script `php local/organization/cli/import_sis.php` will import the data from orbit and create the following:
1. Campuses, buildings, rooms
2. Faculties(as main categories)
3. Departments(as sub categories)
4. Courses
5. Groups(creating cohorts from groups, cohorts are enrolled to courses)
6. Students and teachers





Notice
------
* Make sure you allow role assignment for the SysbindApi role for the following roles: "students","teacher","non-editing teacher"
  on Administration > Users > Allow role assignment



Author
------
SysBind LTD.
