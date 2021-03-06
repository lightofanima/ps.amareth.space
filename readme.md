# ps.amareth.space

This PHP application is designed to increase security by generating
unique passwords for different websites.
These passwords do not change over time and are different for each user,
meaning that if one of your accounts is compromised the others will not be.

It was not designed to be efficient, as I wanted to write it relatively quickly
and to keep the code small. This is normally okay as people don't need to generate
passwords often, but may fall down when thousands of users are generating passwords all the time.
If this is a problem though then you're free to optimise it for your needs :)

## Inspiration
My Spotify account was hacked by a loser from Germany, and I was just happy that I used a different
password on my email accounts for security. However, many of my other accounts shared passwords.
It's really not safe to have one password for everything :)

## Privacy
Only anonymous information is stored in the database for additional features.
It is not possible to extract your passwords, the website you generated passwords for,
or the generated passwords from the database. All information is hashed one-way only.
This means that anyone who hacks the server will not be able to steal your information.
However it does mean that if you forget your two identifying passwords, you will no longer
be able to generate passwords.

## Safety
This code can ideally be run on any machine and will generate the same passwords for
everyone.

To minimise lost passwords, it cleans up user input and does not use installation-specific
information. However, this version may generate different passwords if you
recreate a password with different constraints even if they do not affect the resulting password.
This is due to how the algorithm was implemented. So if you ever have to regenerate your password
ensure that your constraints are the same as before.

However, what I took care to ensure that the system works flawlessly, I can not guarantee
that passwords will not be lost if you do not write them down.

# Installation
To set up this code on your own server, you should just copy these files to a home directory.
You may need to change your database information in dbinfo.php. You must then run the setup.sql
file to create the relevant table in your database. You should make sure not to copy the setup
or test folders, however.

# Changelog

## 1.0.0
* Created initial version of the site.

## 2.0.0
* Found a bug that resulted in the password being of an incorrect length. This fix breaks previous passwords.
* Made minor improvements, such as hiding the password output.
* Fixed different outputs on 32 and 64 bit architectures

## 2.1.0
* Using AJAX to retrieve password to avoid being able to recall the result after closing
* Adding username field and refactoring database to avoid password/site collisions.
* Improving security by no longer storing hashed passwords. If you type the wrong password when retrieving, you'll get the wrong result.
* Moving from md5 to sha+md5.