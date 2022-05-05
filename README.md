# THE BUG

When you have view_component_storybooks storybook path set to `app/components`, `app/components` will no longer be eager loaded, causing issues with view_components - including the first render for every rails session breaking.

Run `bin/rails zeitwerk:check` with this app and you will see the following message:

```
Hold on, I am eager loading the application.

WARNING: The following directories will only be checked if you configure
them to be eager loaded:

  /#{app_location}/view_component_storybook_autoload_bug/app/components

You may verify them manually, or add them to config.eager_load_paths
in config/application.rb and run zeitwerk:check again.

Otherwise, all is good!
```

indicating that no components were eager loaded.
