# Plogger

Plogger (Pietro's Logger) is a simple to initialise logger to get started with your next Rust project.

`plogger` is a wrapper around [env_logger](https://docs.rs/env_logger/latest/env_logger/), with a less configurable - more straight forward - one line initialisation and some sensible defaults.

## Usage

Initialise simple logger as early as you can in your `main()` body by calling:

```rust
use plogger;

fn main() {

    let debug = true; // or false

    plogger::init(debug);
}
```

You can now use the `log`'s crate macros to log from your program:

```rust

fn some_method() {
    log::info!("An info log!");
    log::debug!("A debug log!");
    log::warn!("A warn log!");
}
```

## Docs

Plogger has two modes of operation: normal and debug mode. You can specify which mode you want when initialising the logger via the boolean parameter `debug`.

Plogger always logs to `stdout`, the differences between normal and debug mod include the format of log messages and the level of logs that will be displayed.

### Normal Mode

In normal mode, enabled with `debug=false`, Plogger will only log messages up to `Info` level with the following format:

```
{log timestamp} - {log message}
```

### Debug Mode

In debug mode, enabled with `debug=true`, Plogger will log all messages up to `Debug` level with the following format:

```
{log timestamp} [{log level}] - {log file}:{log line }- {log message}
```
