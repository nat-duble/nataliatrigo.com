Start the Jekyll development server for this site.

## Steps

1. Check if Jekyll is already running on port 4000:
   ```
   lsof -i :4000 | grep LISTEN
   ```
   If a process is listening on port 4000, tell the user the server is already running at http://127.0.0.1:4000 and stop here — skip all remaining steps.

2. Verify Ruby is the right version by running `cat .ruby-version` and `ruby -v`. If there's a mismatch, tell the user and suggest running `rbenv install $(cat .ruby-version) && rbenv local $(cat .ruby-version)`.

3. Run `bundle install` to ensure all gem dependencies are up to date.

4. Start the Jekyll server in the background with live reload:
   ```
   bundle exec jekyll serve --livereload --incremental
   ```

5. Confirm the server is up by checking that output contains "Server address:" and report the local URL to the user (typically http://127.0.0.1:4000).

6. Let the user know they can view the site at that URL and that changes to files will automatically reload the browser.
