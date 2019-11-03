# crypt-baller
Encrypt *.tgz in a given directory with a pgp public key in an automated fashion.

Example:

chmod +x ./crypt-baller

mv ./crypt-baller /usr/local/bin/

gpg --import some-public-key.asc

crontab -e

10 * * * * /usr/local/bin/crypt-baller /mnt/encrypt-me/ public-key-email-or-finger-print@some-place.com

Then you would have another script creating tarballs that are placed in /mnt/encrypt-me/
and ensure they get written to /mnt/encrypt-me/ before the crypt-baller runs against the
directory.

Example tarring action:

( perhaps run each hour in a root crontab 5 minutes after the hour, giving it 5 minutes to complete
before the crypt-baller crontab above encrypts it )

tar czvf /mnt/encrypt-me/$(hostname).logs.$(date +%Y%m%d-%H).tgz /var/log/
