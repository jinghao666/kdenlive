Background: When upgrading to a new version of Kdenlive, there are sometimes issues due to changes to the configuration.

There are two locations for configuration. On Linux:

* `~/.kdenliverc` – single file with settings
* `~/.local/share/kdenlive` – directory with e.g. custom profiles, effect presets, etc.

Some applications, like e.g. JetBrains products, work around this problem by using separate configuration directories for every new version. For Kdenlive, those could be:

```
~/.local/share/kdenlive-24.0.0
~/.local/share/kdenlive-24.0.1
~/.local/share/kdenlive-24.1.0
```

When running a newer version, the user can decide whether to copy existing settings from an older version or whether to start with an empty configuration.

When using existing settings, it may be required to migrate settings, e.g. if a key or even the structure has changed. This can be done the same way as e.g. databases are migrated to a newer version by providing a fuction to migrate from v1 to v2, one from v2 to v3, etc.
