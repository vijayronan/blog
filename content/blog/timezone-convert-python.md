
+++
title = "Timezone Convert Python"
date = 2018-06-23T14:22:24+05:30
tags = ["python","timezone"]
+++

## Install pytz module

```
pip install pytz
```
```
from datetime import datetime
from pytz import timezone

fmt = "%b %d %H:%M"

# Current time in UTC
utc_time = datetime.now(timezone('UTC'))

# Convert to IST time zone
ist_time = utc_time.astimezone(timezone('Asia/Kolkata'))

ist_time = ist_time.strftime(fmt)
print ist_time
```