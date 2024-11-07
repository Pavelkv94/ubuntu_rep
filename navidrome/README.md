The easiest way to convert songs in a directory to a playlist is to change to the directory and run the following command: ls > name-of-playlist.m3u This adds all filenames to a file that is being interpreted as a playlist. After scanning the lib again, Navidrome should show the playlist.

You can utilize the following procedure to generate a token:
Salt (Random string of at least six characters) = c19b2d
Password (Navidrome Password) = sesame
Concatenate Password and Salt = sesamec19b2d
Token (Generate the MD5 hash of 'Concatenated Password and Salt' at md5hashgenerator.com) = 26719a1196d2a940705a59634eb18eab

Widget config:

widget:
type: navidrome
url: https://navidrome.mydomain.com
user: admin
token:26719a1196d2a940705a59634eb18eab
salt: c19b2d