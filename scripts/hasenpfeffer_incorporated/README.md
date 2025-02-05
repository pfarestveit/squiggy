# Copy Squiggy data from prod to a test environment

![Laverne and Shirley at work](../../src/assets/hasenpfeffer_incorporated.jpg)

Real-world data, from production, in a test environment promotes effective testing.

## Pull data from production

```
./scripts/hasenpfeffer_incorporated/pull-data.sh \
  -d db_connection \
  [-a] \
  [-c canvas_hostname [-r replacement_canvas_hostname]]
```

### Available options
```
-d  Database connection information in the form 'host:port:database:username'
-a  [OPTIONAL] Pull all database tables including the canvas table.
-c  [OPTIONAL] Hostname of the Canvas instance for which SuiteC course data
      should be pulled. Defaults to all instances.
-r  [OPTIONAL] If provided, all references to Canvas-hosted resources will
      be changed to this hostname. You must include the '-c' flag when using this option.
```
### Fun facts about _pull-data.sh_

* CSV files are written to the _scripts/hasenpfeffer_incorporated/csv_files_ directory.

## Push data to test environment

```
./scripts/hasenpfeffer_incorporated/push-data.sh -d db_connection [-a] [-i]
```

### Available options
```
-d  Database connection information in the form 'host:port:database:username'
-a  [OPTIONAL] Push all database tables including the canvas table.
-i  [OPTIONAL] Mark all courses as inactive after push. This may be desirable
      when populating a test environment.
```
