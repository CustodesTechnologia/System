After the upgrade, apply this patch to Dispatcher.php

The upgrade process does not set the `installed` field in the
configuration so it always fails this test, yielding the output
that the site setup is still in progress.


