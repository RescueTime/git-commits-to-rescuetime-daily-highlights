#!/bin/sh
#
# An example hook script to log commit messages
# as a 'daily highlight' in RescueTime Premium
#
# See README.md for more information
#
# To enable this hook:
#
# 1. Place this file in .git/hooks and rename to "post-commit".
#
# 2. Update the value of API_KEY below with a valid RescueTime API key.
#    [ you can generate a key at https://www.rescuetime.com/anapi/manage ]

API_KEY=PUT_YOUR_API_KEY_HERE

# REQUIRED FIELDS - Today's date and commit message

MESSAGE=$(git log -1 HEAD --pretty=format:%s)
DATE_TODAY=$(date +"%Y-%m-%d")

# You can edit the LABEL value if you would rather
# describe these commits differently.

LABEL='Code Commit'

# See more filtering examples in README.md

if [[ ${#MESSAGE} -gt 16 ]]; then
  curl --data "key=$API_KEY&highlight_date=$DATE_TODAY&description=$MESSAGE&source=$LABEL" https://www.rescuetime.com/anapi/highlights_post
fi
