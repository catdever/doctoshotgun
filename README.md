# DOCTOSHOTGUN

This script lets you automatically book a vaccine slot on Doctolib for today or
tomorrow, following rules from the French Government.


## Python dependencies

- [woob](https://woob.tech)
- cloudscraper
- dateutil
- termcolor

## How to use it

Install dependencies:

```
pip install -r requirements.txt
```

Run:

```
./doctoshotgun.py <city> <email> [password]
```

For example:

```
$ ./doctoshotgun.py paris roger.philibert@gmail.com
Password:
Starting to look for vaccine slots for Roger Philibert...
This may take a few minutes/hours, be patient!

Center GHU Paris Vaccination Covid-19:
– Sainte-Anne... first slot not found :(
– Pierre Bayle ... first slot not found :(

Center Centre de Vaccination Covid 19 - Ville de Paris:
– Centre de Vaccination - Mairie du 10e... found!
  ├╴ Best slot found: Mon May 17 16:30:00 2021
  ├╴ Second shot: Sat Jun 26 17:00:00 2021
  ├╴ Booking for Roger Philibert...
  └╴ Booking status: True

💉 Booked! Congratulation.
```

Optional arguments:

```
--center "<center_name>" [--center "<other_center>" …]  : filter centers to only choose one from the provided list
--patient <index>                                       : select patient for which book a slot
--debug                                                 : display debug information
```

### Multiple cities

You can also look for slot in multiple cities at the same time. Cities must be separated by commas:

```
$ ./doctoshotgun.py <city1>,<city2>,<city3> <email> [password]
```

### Filter on centers

You can give name of centers in which you want specifictly looking for:

```
$ ./doctoshotgun.py paris roger.philibert@gmail.com \
      --center "Centre de Vaccination Covid 19 - Ville de Paris" \
      --center "Centre de Vaccination du 7eme arrondissement de Paris - Gymnase Camou"
```

### Select patient

For doctolib accounts with more thant one patient, you can select patient just after launching the script:

```
$ ./doctoshotgun.py paris roger.philibert@gmail.com PASSWORD
Available patients are:
* [0] Roger Philibert
* [1] Luce Philibert
For which patient do you want to book a slot?
```

You can also give the patient id as argument:

```
$ ./doctoshotgun.py paris roger.philibert@gmail.com PASSWORD -p 1
Starting to look for vaccine slots for Luce Philibert...
```


## Development

### Running tests

```
 $ pip install -r requirements-dev.txt
 $ pytest test_browser.py
```
