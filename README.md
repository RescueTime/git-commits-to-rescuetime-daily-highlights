Log Git commit messages as RescueTime Daily Highlights
==========================================

An example script to show how to log code commits as Daily Highlights in RescueTime

Daily highlights are a part of RescueTime Premium that allows you to keep a log of the things you are accomplishing.
You can learn more on the [RescueTime website](https://www.rescuetime.com/rescuetime-pro?detail=highlights)

Highlights can be entered manually on the website, or submitted programmatically via the API. This script shows how to use a Git post-commit hook to log a highlight.

## To use this script

1. Copy the file `post-commit.sample` into your `.git/hooks` directory and rename it to `post-commit`
2. Update the `API_KEY` value to use a valid RescueTime API key - [More info](https://www.rescuetime.com/anapi/manage)
3. Add any logic you'd like to use to restrict when highlights are logged
4. Save the file and make sure it's executable

After you commit your code, you should see highlights start to show up [here](https://www.rescuetime.com/daily-highlights).

## Configuration

### LABEL field:

This will collapse commits under a common label, which is quite helpful if you have a lot of commits. If omitted all commit messages will be shown at the top level alongside any highlights you enter manually on the website.

If you would like to use a different label, change this value to any singular noun. You may, for example, want to reflect the repository in your label if you work on multiple projects - "Rails Commits".

### Filtering highlights

You may not want to log all commit messages, especially if they are just for small changes.

**Examples:**

To ignore a short commit message:

    if [[ ${#MESSAGE} -gt 15 ]]; then

To ignore a commit message containing the string '_IGNORE_':

    if [[ "$MESSAGE" != *_IGNORE_* ]]; then

To ignore both of the above conditions:

    if [[ ${#MESSAGE} -gt 15 && "$MESSAGE" != *_IGNORE_* ]]; then
