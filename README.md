# This tutorial is based on https://github.com/markshust/docker-magento. Give him a star for helping us with docker-magento.

Follow these steps:

- Fork my repo: https://github.com/dotrongbinhf/magento2

- Clone your forked repo into your magento2 folder
``` bash
git clone https://github.com/your_github_name/your_forked_repo.git
```

``` bash
cd /path-to-your-magento2-folder/magento2
```
- Create /src/app/design/frontend/Magento folder and /src/app/design/adminhtml/Magento folder

- Start some containers, copy files to them and then restart the containers:
``` bash
bin/start --no-dev
bin/copytocontainer --all ## Initial copy will take a few minutes...
```

- Import existing database:
``` bash
bin/mysql < ./initial-Magento-data.sql
```

- Import app-specific environment settings:
``` bash
bin/magento app:config:import
## Don't worry if its say nothing to import, its normal
```

- Create a DNS host entry and setup Magento base url
``` bash
bin/setup-domain yoursite.test

bin/restart

open https://magento.test
```