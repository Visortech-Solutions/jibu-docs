# Add a sample workflow.

A sample workflow that sends an SMS on course completion has been created. This can be duplicated for other events which trigger an SMS.

1.  On your local machine, create a file named `Course_Completed_SMS.json`.
2.  Add the following content to the file and save.

    ```
    {"name":"Course Completion SMS","description":"{\"text\":\"<p dir=\\\"ltr\\\" style=\\\"text-align: left;\\\">SMS Sent on course completion<br><\\\/p>\",\"format\":\"1\"}","event":"\\core\\event\\course_completed","debug":"1","steps":{"9":{"id":"9","name":"User phone number","description":"Find the phone number of the user who has enrolled to a course","type":"lookups","stepclass":"\\tool_trigger\\steps\\lookups\\user_lookup_step","data":"{\"useridfield\":\"userid\",\"outputprefix\":\"user_\",\"nodeleted\":\"1\",\"stepdesc\":\"User lookup\",\"typedesc\":\"Lookup\"}","steporder":"0"},"10":{"id":"10","name":"Find course","description":"Find the course id of the course they enrolled to","type":"lookups","stepclass":"\\tool_trigger\\steps\\lookups\\course_lookup_step","data":"{\"courseidfield\":\"courseid\",\"outputprefix\":\"course_\",\"stepdesc\":\"Course lookup\",\"typedesc\":\"Lookup\"}","steporder":"1"},"11":{"id":"11","name":"Send SMS","description":"Send SMS to user on enrollment","type":"actions","stepclass":"\\tool_trigger\\steps\\actions\\http_post_action_step","data":"{\"url\":\"https:\\\/\\\/api.textit.in\\\/api\\\/v2\\\/broadcasts.json\",\"httpheaders\":\"Authorization: Token f1a013b6ea6ead9af3d5fd858b46d67b6ad7d61e\\r\\nContent-Type: application\\\/json\",\"httpparams\":\"{\\\"text\\\":\\\"Congratulations! You have completed {course_fullname}. We hope that this course was helpful to you.\\\",\\\"urns\\\":[\\\"tel:{user_phone2}\\\"]}\",\"jsonencode\":\"0\",\"expectedresponse\":\"201\",\"stepdesc\":\"HTTP Post\",\"typedesc\":\"Action\"}","steporder":"2"}},"moodleversion":"2020061503","pluginversion":"2021030400"}
    ```

3.  Go to Site administration > Plugins > Admin tools > Event Trigger > Manage.
4.  Click on Import a workflow > Choose a file, choose the file created in step 1 and click on `Save Changes`.
    ![Screenshot](../img/eventtrigger-choose-file.png)
5.  After the file has been imported, it will appear in the list of workflows. The workflow can then be duplicated and edited to suit other events.
    ![Screenshot](../img/eventtrigger-workflows.png)
