[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

# g2pH: Deep Learning English Grapheme To Phoneme Interpretation for Heteronyms

This module is designed to convert detected Heteronyms from graphemes (spelling) to phonemes (pronunciation).
It is mainly intended for use with speech synthesis, where a traditional dictionary would not be able to identity different pronunciations.

Hetreonyms are two or more words that are spelled identically but have different sounds and meanings.

Example of heteronyms:

* Did you want to read the book? I thought you read it already. (/rēd/ as present-tense vs. /red/ as past-tense)
* The soldier was to desert the army and venture into the desert. (/ˈdezərt/ as noun vs. /dəˈzərt/ as verb)

The conversion is handled by a deep learning seq2seq framework based on TensorFlow.

Words not matching the [preset list](g2p_h/heteronyms.en) of known heteronyms are not converted to phonemes.
This allows them to be handled by other dictionaries downstream or by models directly.

## Environment

* python 3.x

## Dependencies

* numpy >= 1.13.1
* nltk >= 3.2.4
* python -m nltk.downloader "averaged_perceptron_tagger" "cmudict"
* Distance >= 0.1.3

## Example Usage

    from g2p_h import G2p
    
    texts = ["I refuse to collect the refuse around here."]
    g2p = G2p()
    for text in texts:
        out = g2p(text)
        print(out)
    >>> ['AY1', ' ', 'R', 'IH0', 'F', 'Y', 'UW1', 'Z', ' ', 'T', 'UW1', ' ', 'K', 'AH0', 'L', 'EH1', 'K', 'T', ' ', 'DH', 'AH0', ' ', 'R', 'EH1', 'F', 'Y', 'UW2', 'Z', ' ', 'ER0', 'AW1', 'N', 'D', ' ', 'HH', 'IY1', 'R', ' ', '.']


## References
* [Learning pronunciation from a foreign language in speech synthesis networks](https://arxiv.org/abs/1811.09364)
* Kyubyong Park & [Jongseok Kim](https://github.com/ozmig77)
