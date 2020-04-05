# Cluster and Cloud Computing - Assignment 1

## TODO

- Get latest list of supported languages from Twitter, especially for code "und"

- Setup Code Linter

## Part 1: Identification of common hashtags

- Identify the top 10 most commonly used hashtags and the number of times they appear. A matching hashtag string can match if it has upper/lower case exact substrings, e.g. #covid19 and #COVID19 are a match. A hashtag should follow the Twitter rules, e.g. no spaces and no punctuation are allowed in a hashtag.
Any string following a # up until a space or punctuation character is a valid hashtag string (except underscore _). Upper/lower case can still be a match, i.e. '#covid19' and '#COVID19'.

-> use   ["doc"]["entities"]["hashtag"] for matching
-> ignore empty strings
-> #covid19 is a match with '#COVID19' and '#covid19,' and '#covid19-' and '#COVID19#' etc-
->There is one thing that occurs to me now that the assignment is set - how short can a substring be? For example, '#c' is a valid substring that will match all things beginning with 'c' and hence may well be in the top 10

To address this, there should be some hashtags (strings) that end with a space ( _ ). Thus "#covid19 " (note the space at the end) have to be included in the top 10, else it is not a hashtag. Ok?


-> Optional: investigate hashtags in user profile description

```
string.punctuation = r"""!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~""" from python
```

## Part 2: Language counting

- Identify the languages used for tweeting and the number of times the language is used for the provided tweets

Documentation: https://developer.twitter.com/en/docs/twitter-for-websites/twitter-for-websites-supported-languages/overview

Standard for language code: https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes

Standard for country code: https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2






## Notes

Set each process to read parts of the file (use line delimeter) and gather results in master process.

"Make sure to use a wall size that is neither too long or too short. If to long, it will never get scheduled, and if too short, it will be canceled before finishing.

What if 2 languages or hashtags have the same count number when ranking?  -> Show top 11 hashtags

## SPARTAN partitions

**Cloud**

This partition is best suited for general-purpose single-node jobs. Multiple node jobs will work, but communication between nodes will be comparatively slow.

**Physical**

Each node is connected by high-speed 25Gb networking with 1.15 µsec latency, making this partition suited to multi-node jobs (e.g. those using OpenMPI).

You can constrain your jobs to use different groups of nodes (e.g. just the Intel(R) Xeon(R) Gold 6154 CPU @ 3.00GHz nodes) by adding #SBATCH --constraint=physg4 to your submit script

## Troubleshooting

Python/3.7.1 outputs error messages, use Python/3.4.3 instead.

```
No OpenFabrics connection schemes reported that they were able to be used on a specific port As such, the openib BTL (OpenFabrics support) will be disabled for this port.
```