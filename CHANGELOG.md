# Changelog

## v0.1.0
+ Added - Support for exclusion selectors in analysis-archive rules in the add/update command
+ Added - Support for "Max Images Per Account" setting in analysis-archive rule creation 
+ Added - Support for NeXTLinux False Positive management feature to add/list/remove artifact corrections.
+ Improved - Update to use UBI 8.3 base image for Docker image instead of UBI 8.2. Fixes #163 
+ Improved - Update PyYAML version from 5.3.1 to 5.4.1. Fixes #155
+ Fixed - Event list filtering by level fixed to correctly support the filters. Fixes #141
+ Fixed - Corrected archive get and delete command help. Fixes #142
+ Fixed - Remove wait for disabled group records in a feed or disabled feedss for system wait
