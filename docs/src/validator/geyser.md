---
titwe: sowana vawidatow geysew p-pwugins
sidebaw_wabew: g-geysew p-pwugins
pagination_wabew: v-vawidatow g-geysew pwugins
---

## o-ovewview

v-vawidatows u-undew heavy wpc woads, (⑅˘꒳˘) such as when sewving getpwogwamaccounts cawws, /(^•ω•^)
can faww behind the nyetwowk. rawr x3 t-to sowve this pwobwem, (U ﹏ U) the vawidatow has been
e-enhanced to suppowt a pwugin mechanism, (U ﹏ U) c-cawwed a "geysew" pwugin, (⑅˘꒳˘) thwough which
the infowmation a-about accounts, òωó swots, ʘwʘ bwocks, a-and twansactions c-can be
twansmitted to extewnaw data stowes such as wewationaw databases, /(^•ω•^) nyosqw
d-databases ow kafka. ʘwʘ wpc sewvices then can be devewoped to consume data fwom
these e-extewnaw data stowes with the p-possibiwity of m-mowe fwexibwe and t-tawgeted
optimizations s-such as caching and indexing. this awwows t-the vawidatow to focus
on pwocessing twansactions w-without being swowed down by busy wpc wequests. σωσ

this document descwibes the intewfaces of t-the pwugin and the wefewentiaw p-pwugin
impwementation f-fow the postgwesqw d-database. OwO

[crates.io]: https://crates.io/search?q=solana-
[docs.rs]: https://docs.rs/releases/search?query=solana-

### Important Crates:

- [`uwuave-geyser-plugin-interface`] &mdash; This crate defines the plugin
interfaces.

- [`solana-accountsdb-plugin-postgres`] &mdash; The crate for the referential
plugin implementation for the PostgreSQL database.

[`uwuave-geyser-plugin-interface`]: https://docs.rs/uwuave-geyser-plugin-interface
[`solana-accountsdb-plugin-postgres`]: https://docs.rs/solana-accountsdb-plugin-postgres
[`solana-sdk`]: https://docs.rs/solana-sdk
[`solana-transaction-status`]: https://docs.rs/solana-transaction-status

## The Plugin Interface

The Plugin interface is declared in [`uwuave-geyser-plugin-interface`]. It
is defined by the trait `GeyserPlugin`. The plugin should implement the
trait and expose a "C" function `_create_plugin` to return the pointer to this
trait. For example, in the referential implementation, the following code
instantiates the PostgreSQL plugin `GeyserPluginPostgres ` and returns its
pointer.

```
#[no_mangle]
#[allow(improper_ctypes_definitions)]
/// # Safety
///
/// This function returns the GeyserPluginPostgres pointer as trait GeyserPlugin.
pub unsafe extern "C" fn _create_plugin() -> *mut dyn GeyserPlugin {
    let plugin = GeyserPluginPostgres::new();
    let plugin: Box<dyn GeyserPlugin> = Box::new(plugin);
    Box::into_raw(plugin)
}
```

A plugin implementation can implement the `on_load` method to initialize itself.
This function is invoked after a plugin is dynamically loaded into the validator
when it starts. The configuration of the plugin is controlled by a configuration
file in JSON5 format. The JSON5 file must have a field `libpath` that points
to the full path name of the shared library implementing the plugin, and may
have other configuration information, like connection parameters for the external
database. The plugin configuration file is specified by the validator's CLI
parameter `--geyser-plugin-config` and the file must be readable to the
validator process.

Please see the [config file](#config)