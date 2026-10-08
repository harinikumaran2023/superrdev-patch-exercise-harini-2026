# Patch Notes

## Summary
Fixed the task status filter in the backend repository query. The original SQL did not group the title/description search conditions before applying the optional status condition. Because SQL evaluates AND before OR, tasks matching the title could bypass the status filter. I added parentheses around the title/description OR condition so archived and status conditions apply consistently.

## What I Did Not Change
I did not modify unrelated frontend behavior, database schema, or the Oracle PL/SQL reference artifact. The goal was to keep the patch focused on the confirmed functional defect.

## Biggest Remaining Risk
The project has limited automated test coverage, so future changes to search, filtering, and pagination could introduce regressions. An automated integration test for combined search and status filtering would reduce this risk.

## Tools / AI Used
Used VS Code, PowerShell, Git, browser/API testing, and AI assistance for debugging, reasoning about the SQL condition, and validating the focused fix.