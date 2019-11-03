# crypt-baller
Encrypt *.tgz in a given directory with a pgp public key in an automated fashion.

Example:

chmod +x ./crypt-baller

mv ./crypt-baller /usr/local/bin/

gpg --import some-public-key.asc

crontab -e

10 * * * * /usr/local/bin/crypt-baller /mnt/encrypt-me/ public-key-email-or-finger-print@some-place.com
