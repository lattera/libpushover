# libpushover

libpushover is a modern C library for the
[Pushover](https://pushover.net/) service. Since its primary use case
is with HardenedBSD's infrastructure monitoring daemon, portability to
other operating systems (eg, Linux) is not a priority. However, if
someone wants to punish themselves by porting to Linux, patches are
gladly accepted for review.

libpushover depends on only one library: libcurl. Eventual migration
away from libcurl to libfetch is planned.

## Example Usage

The following code sample illustrates how easy it is to use
libpushover:

```
#include <err.h>
#include <libpushover.h>

pushover_message_t *msg;
pushover_ctx_t *ctx;

ctx = pushover_init_ctx("Pushover API Token");
if (ctx == NULL) {
	errx(1, "Pushover init failed.");
}

msg = pushover_init_message(NULL);
if (pmsg == NULL) {
	errx("Pushover message init failed.");
}

pushover_message_set_dest("Destination token");
pushover_message_set_title("Message title");
pushover_message_set_msg("Message body content");
pushover_submit_message(ctx, msg);

pushover_free_message(&msg);
pushover_free_ctx(&ctx);
```
