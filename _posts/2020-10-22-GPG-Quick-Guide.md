---
title: GPG quick guide
published: true
---

Hi! I've just configured GPG and I thought I might as well post a quick guide on how to use it.

GNU Privacy Guard (GnuPG or GPG) is an encryption program that provides cryptographic privacy and authentication for data communication. It's used for signing, encrypting, and decrypting texts, files, e-mails and such.

GPG is a replacement for Symantec's PGP (Pretty Good Privacy). They both are interoperable implementations of the OpenPGP standards. I chose to go with GPG because I'm biased toward free and open source software.

After you download and install GPG on your operation system of choice, here are a few commands you might find useful:

\# Check GPG version

    gpg --version

\# List public keys you have stored (yours and other people's keys)

    gpg --list-keys

\# List private keys (generally only your own)

\# The ID is the hexadecimal number listed

    gpg --list-secret-keys

\# Create a new private key

\# It will ask for a passphrase, your name and e-mail

    gpg --gen-key

\# Export public key to file

    gpg --armor --output "key.txt" --export "YOUR-NAME"

\# Publish public key to server

\# MIT is just an example

    gpg --keyserver hkp://pgp.mit.edu --send-keys XXXXXXXX

\# Export private key to file, for backup purposes

\# Keep it secret!

\# Replace XXXXXXXX with your hexadecimal key ID

\# Omitting the \-\-armor flag will give you binary output instead of ASCII

    gpg --export-secret-keys --armor XXXXXXXX > ./my-priv-gpg-key.asc

\# Delete private keys from local storage

    gpg --delete-secret-keys XXXXXXXX

\# Delete public keys from local storage

    gpg --delete-keys XXXXXXXX

\# Import public key or private key from file

\# This works the same for binary or ASCII (armored) versions of keys

    gpg --import ./my-priv-gpg-key.asc

\# Import public key or private key from server

\# For example, import the DevDungeon/NanoDano public GPG key from MIT

    gpg --keyserver pgp.mit.edu  --recv C104CDF0EDA54C82

\# Import NanoDano's public GPG key

    gpg --keyserver pgp.mit.edu --search-keys nanodano@devdungeon.com

**Encrypt message symmetrically (passphrase)**

\# Options: \-\-armor, \-\-cipher-algo "ALGO-NAME (e.g. AES256)", \-\-output "output.txt.gpg (or .asc if armored)"

    gpg --symmetric message.txt

\# Encrypt and sign (all in a single output file)

    gpg --sign --symmetric message.txt

**Encrypt message asymmetrically**

\# This will prompt and ask the recipient's ID or email address, if you don't specify it upfront

\# Options: -r "RECIPIENT-EMAIL-ADDRESS", \-\-armor, \-\-output "output.txt.gpg (or .asc if armored)"

\# Default encrypted output will be in message.txt.gpg (or .asc if armored)

    gpg --encrypt message.txt

\# Encrypt and sign at the same time

    gpg --encrypt --sign message.txt

**Decrypt message**

\# Automatically detects and verifies signature, symmetry, key, may prompt for passphrase

\# Options: > decrypted.txt (redirect output to file)

    gpg -d message.txt.gpg

**Sign a message**

\# Options: \-\-sign instead of \-\-clearsign in order to obtain binary output

    gpg --clearsign message.txt

\# Can be verified with --decrypt

\# They are not _actually_ encrypted

\# This will print out the message along with the signature info

    gpg --decrypt message.txt.gpg
    gpg --decrypt message.txt.asc

**Encrypt and sign a message**

\# Symmetric encrypt with signature

    gpg --sign --symmetric message.txt

\# Asymmetric encrypt with signature

    gpg --sign --encrypt --recipient RECIPIENT-EMAIL message.txt

**Verify signatures**

\# When you decrypt the message it will verify the signature

    gpg --decrypt message.txt.asc  

\# Verify a signed message that included a signature

    gpg --verify message.txt.asc

\# Verify and extract original document

    gpg --output message.txt message.txt.asc

**Detached signatures**

\# Create a separate signature file

\# Will create message.txt.sig

    gpg --detach-sign message.txt

\# This verify will automatically check the signature against a file named "message.txt"

    gpg --verify message.txt.sig

\# Specify the file to check it against

    gpg --verify some_signature.sig ./message.txt

You can check out my public key on my About page

[Based on this guide by NanoDano](https://www.devdungeon.com/content/gpg-tutorial)
