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

Parameters:
```
--center "<center_name>" [--center "<other_center>" …]  : filter centers to only choose one from the provided list. 
```

For example:

```
$ ./doctoshotgun.py paris roger.philibert@gmail.com
Password:
::: Trying to find a slot in Centre de Vaccination Covid 19 - Ville de Paris
::: Best slot found: Mon May 17 11:00:00 2021
::: Second shot: Fri Jun 25 15:20:00 2021
::: Booking for Roger Philibert...
::: Booking status: True
::: Booked!
```

You can also look for slot in multiple cities at the same time. Cities must be separated by commas.

Run:

```
./doctoshotgun.py <city1>,<city2>,<city3> <email> [password]
```

For doctolib accounts with more thant one patient, you can select patient just after launching the script :

```
$ ./doctoshotgun.py paris roger.philibert@gmail.com PASSWORD
Available patients are:
* [0] Roger PHILIBERT
* [1] Luce PHILIBERT
For which patient do you want to book a slot ?
```
You can also give the patient id as argument :
```
$ ./doctoshotgun.py paris roger.philibert@gmail.com PASSWORD -p 1
Selected patient : [1] Luce PHILIBERT
```


## Development

### Running tests

```
 $ pip install -r requirements-dev.txt
 $ pytest test_browser.py
```
