# SyncRuleEditor
Custom Sync Rule Editor for AAD Connect

This project is designed to provide a proxy EXE for the AAD Connect sync rule editor application.

When the AAD Connect sync rule editor proxy is first launched, it will create a self-signed cert in the local machine certificate store 
used for asymetric encryption of passwords.

The tool will then prompt for a password, and if this is the first run, it will notify and then encrypt the password and store it in the registry.

Next, it will create an Application event log source called SyncRuleEditor and log a 411 Informational that a user has launched the editor.

Lastly, it will perform a backup of the current sync rules and ZIP them to the TEMP folder and launch the SyncRuleEditor.

Subsequent launches of the tool will prompt for password, confirm, and throw a 412 Error in the event log if unsuccessful, otherwise it will
perform a backup of the rules as a ZIP and launch the editor.

Latest download release can be located here :

https://github.com/dakegg/SyncRuleEditor/releases/tag/Release

Update 25 July 2018 - fixed an issue where the eventlog, if absent of any events, would return an error the source was not registered and the application would try to create the source again, resulting in an error.

Update 25 July 2018 - added a second version of the tool that is a log-only.  It will not create the PW or prompt, it will simply log to the eventlog and make a backup.
