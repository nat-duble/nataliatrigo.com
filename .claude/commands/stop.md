Stop the Jekyll development server for this site.

## Steps

1. Find the Jekyll server process:
   ```
   pgrep -f "jekyll serve"
   ```

2. If a process is found, kill it:
   ```
   pkill -f "jekyll serve"
   ```

3. Confirm it stopped by running `pgrep -f "jekyll serve"` again — it should return no output.

4. Let the user know the server has stopped. If no process was found in step 1, let them know it wasn't running.
