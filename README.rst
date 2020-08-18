
ElectrumX Banner Updater
------------------------

This script can be used to update the ElectrumX banner file to contain information about memory pool and fees.

ElectrumX server:
    https://github.com/kyuupichan/electrumx

Groestlcoin Core daemon:
    https://github.com/groestlcoin/groestlcoin


Getting Started
---------------
``sudo apt-get install curl -y``
``touch /home/electrum-grs/banner && cd /root && git clone https://github.com/Groestlcoin/electrumx-banner-updater && cd electrumx-banner-updater && chmod +x update-electrumx-banner && ./update-electrumx-banner ``
``nano /etc/electrumx-grs.conf``

Add this:
BANNER_FILE=/home/electrum-grs/banner

Also make sure this line is present:
SERVICES=tcp://:51001,ssl://:51002,wss://:51004,rpc://

Save and close the editor and restart electrumx: ``service electrumx-grs restart``

The first time you run this script your original banner file will be copied to ``${BANNER}.template``.

On each subsequent run ``${BANNER}.template`` will be used as the top portion of the new banner.

If you wish to change your banner you should edit ``${BANNER}.template``.


Edit update-electrumx-banner:
*****************************

- Adjust the ``GROESTLCOIN_DATADIR`` environment to specify where to find your groestlcoin data directory.

- Adjust the ``GROESTLCOIN_CLI`` environment to specify where to find groestlcoin-cli.

- Adjust the ``BANNER`` environment to specify the your electrumx banner file.


Scheduled Update:
*****************

Run ``crontab -e`` and add a cron job to update the banner every 2 minutes.

::

    */2 * * * *  /path/to/update-electrumx-banner


Versions
--------

This script is working with the following software versions::

 Operating System:   Ubuntu 18.04
 ElectrumX:          1.11.0
 Groestlcoin Core:   2.19.1
