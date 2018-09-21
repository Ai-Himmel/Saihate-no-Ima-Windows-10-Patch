# Saihate-no-Ima-Windows-10-Patch

Some friends have told me that Saihate no Ima can be only run in Windows 10 in Japanese language.

So I took some time to debug and finally found out the reason.

It is because certain function in this game, which aim to get the font name from the system, returns a normal string like `MS Gothic`.And the program compares it with a SHIFT_JIS string like `ＭＳ ゴシック`.

That is really a simple question.And the solution is just patch the SHIFT_JIS coded string with normal one.

There are two places to be patched in this program.

One is `82 6C 82 72 20 83 53 83 56 83 62 83 4E`(ＭＳ ゴシック),and patch it into `4D 53 20 47 6F 74 68 69 63 00`(MS Gothic).(Just ignore the rest bytes of raw string and cut with 00 ^_^)

Another is `82 6C 82 72 20 82 6F 83 53 83 56 83 62 83 4E`(ＭＳ Ｐゴシック),and patch in into `4D 53 20 50 47 6F 74 68 69 63 00`(MS PGothic)

Everything just looks like working fine after patching(with Locale Emulator).

And the file in this repo is patched from Saihate no Ima complete (最果てのイマ COMPLETE) version.

The solution may be the same for other versions but I have never tested.

![](https://i.loli.net/2018/09/17/5b9e7f342b4dd.png)
