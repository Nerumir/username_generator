# OSINT - Username Generator
OSINT tool to generate potential usernames based on target informations

> [!IMPORTANT]
> This script only needs `argparse` to work and is part of the default Python librairy, so you shouldn't have Python package to install.

This tool is use to generates potential usernames based on :

- First name (supports compound names)
- Last name
- Birthday date
- Already known usernames of target

> [!NOTE]
> None of those informations are mandatory, the generator will do the best he can according to supplied informations.

There is multiple a flag `-m` to generate potential mails instead of usernames. Be aware that the quantity of mails generated will be huge (at least around 100k). This is used to find in a potential local database of emails that you could have. If the database is indexed on mails, it should be matched with real data in a reasonnable amount of time.

There is 4 modes : XL, L, M and S. They all correspond to a certain level of variations in generated usernames. To have a rough idea of the quantity of usernames generated if all the informations about the target is provided and we have 2 already existing usernames for that target :

- XL : Most usernames possible **(~1392)**
- L : Less date formats and no mixed separators **(~360)**
- M : Without usernames that have 1 to 9 added at the end (that are added to discover potential secondary accounts) **(~144)**
- S : Without dates **(~24)**

> [!TIP]
> Those tests were ran with the following command : `python username_generator.py -f jean -l doe -b '13/12/1998' -u 'nerumir,phaeryl' -s xl | wc -l`

Here the following `--help` output for the script :

```
usage: Username generator [-h] [-f FIRSTNAME] [-l LASTNAME] [-b BIRTHDATE] [-u USERNAMES] [-m] [-s SIZE]

This script generates potential usernames based on information on target. It can generate potential emails too and verify if it exists.

options:
  -h, --help            show this help message and exit
  -f FIRSTNAME, --firstname FIRSTNAME
                        First name (optional). Supports compound names (generates 6x more potential usernames)
  -l LASTNAME, --lastname LASTNAME
                        Last name (optional)
  -b BIRTHDATE, --birthdate BIRTHDATE
                        Birth date (dd/mm/YYYY or dd/mm) (optional)
  -u USERNAMES, --usernames USERNAMES
                        Known usernames of the target (comma separated) (optional)
  -m, --mails           Put this flag if you desire to generate potential mails of the target instead of generating usernames. There will be a lot of them but can be compared with mails in data
                        breaches (optional)
  -s SIZE, --size SIZE  Amount of potential usernames generated (xxl, l, m or s) (default is "m"). "l" = Less date formats and no mixed separators. "m" = Without usernames that have 1 to 9 added at
                        the end (potential secondary accouts). "s" = Without dates
```
