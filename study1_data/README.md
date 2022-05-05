# Overview

The data contained in `study1_data.csv` were collected and reported by McCurdy et al. (2020). The dataset contains German speaker responses to the task of inflecting novel nouns (developed by Marcus et al., 1995) into their plural form. The data contains both production and acceptability ratings for the same stimuli. Please refer to the paper, especially Appendix A, for details on data collection methods.

# Fields

The CSV file contains the following fields (with data type and short description):

- Time of study session
	- `StartDate`
		- Timestamp 
		- Indicates when participant begain the study
	- `EndDate`
		- Timestamp 
		- Indicates when participant concluded the study
	- `Duration..in.seconds.`
		- Integer
		- Duration in seconds of study session for participant, automatically calculated by the survey provider (Qualtrics)
- Subject properties, preceded by `S_`
	- `S_Participant_ID`
		- UUID
		- Anonymous identifier assigned to a unique participant
	- `S_Consent`
		- Binary (0, 1)
		- 1 indicates consent to participate in study, including data release
	- `S_Age`
		- Integer (Likert scale)
		- Subject reported age bracket, with the following levels:
			- 1 | Under 18
			- 2 | 18-24
			- 3 | 25-34
			- 4 | 45-54
			- 5 | 55-46
			- 6 | 65+
	- `S_EN_Level`
		- Integer (Likert scale)
		- Subject reported level of English proficiency, with the following levels (corresponding to CEFR designations):
			- 1 | No English proficiency
			- 2 | A1
			- 3 | A2
			- 4 | B1
			- 5 | B2
			- 6 | C1
			- 7 | C2
			- 8 | Native speaker of English
	- `S_EN_Exposure`
		- Integer (Likert scale)
		- Subject reported typical level of English exposure ("Roughly how often per week do you hear, speak, or read English?"):
			- 1 | Less than an hour per week
			- 2 | 1-2 hours / week
			- 3 | 2-5 hours / week
			- 4 | 5-10 hours / week
			- 5 | 10+ hours / week
	- `S_L1`
		- Text
		- Subject reported native language 
	- `S_L2s`
		- Text
		- Subject reported second language proficiency other than English
- Subject response to introductory onboarding task of inflecting existing German words. Field format: `OB_` (for 'onboarding'), followed by the target word to inflect.
	- `OB_Messe`
		- Text
		- Correct form: "Messer"
	- `OB_Teil`
		- Text
		- Correct form: "Teile"
	- `OB_Fach`
		- Text
		- Correct form: "Fächer"
	- `OB_Kind`
		- Text
		- Correct form: "Kinder"
	- `OB_Floß`
		- Text
		- Correct form: "Flöße"
	- `OB_Klöster`
		- Text
		- Correct form: "Klöster"
	- `OB_Bett`
		- Text
		- Correct form: "Betten"
- Questions of interest to the study, based on the wug stimuli developed by Marcus et al. (1995)
	- `Q_Task`
		- Text
		- Category of task. One of the following:
			- "production" - subject produces a plural form
			- "rating" - subject rates the acceptability of a plural form
			- "check" - attention check
	- `Q_ID`
		- Text
		- Unique identifier for question
	- `Q_Response`
		- Task-dependent
			- if `Q_Task` = "production": text string
			- if `Q_Task` = "rating" or "check": integer (Likert scale)
		- Subject response to production or rating task. If production, the response is the plural form of the provided word. If rating, it is an acceptability rating on a Likert scale with the following levels:
			- 1 | Very bad
			- 2 | Bad
			- 3 | Not good, not bad
			- 4 | Good
			- 5 | Very good
	- `Q_Lemma`
		- Text
		- Novel noun from Marcus et al. (1995) stimuli. N.B. the nouns are in lowercase here for ease of data processing; when presented in the study, they were capitalized as is standard for German nouns (e.g. *Das Bral*).
	- `Q_Lemma_HasRhymes`
		- Logical (True, False)
		- True if Q_Lemma is in the "Rhymes" category (i.e. rhymes with existing German nouns), False if Q_Lemma is in the "Non-Rhymes" category
	- `Q_PL_Form`
		- Text
		- Plural form of M95 noun.
			- if `Q_Task` = "production": plural form produced by subject
			- if `Q_Task` = "rating" or "check": plural form presented to subject for rating
	- `Q_PL_Label`
		- Text
		- Classification of `Q_PL_Form` into one of 9 classes (considering umlaut):
			- e
			- umlaut_e
			- en
			- er
			- umlaut_er
			- zero
			- umlaut (equivalent to umlaut_zero)
			- s
			- other
	- `Q_PL_HasUmlaut`
		- Logical (True, False)
		- True if `Q_PL_Label` includes "umlaut"; False if not
	- `Q_PL_Suffix`
		- Text
		- Classification of `Q_PL_Form` into one of 6 classes (ignoring umlaut):
			- e
			- en
			- er
			- zero
			- s
			- other


## Order of question presentation 

Note that the order of the fields in the data does not reflect the order of presentation in the study --- they have been rearranged to a "long" format for easier analysis. For questions with responses from subjects, the order of presentation was as follows:

- Study overview
	- `S_Consent`
- Study introduction and onboarding
	- `OB_*`
- Production task
	- Questions where `Q_Task` = "production"
- Rating task
	- Questions where `Q_Task` = "rating" or "check"
- Background survey
	- `S_EN_Level`
	- `S_EN_Exposure`
	- `S_L1`
	- `S_L2s`
	- `S_Age`

# References

Gary  F  Marcus,  Ursula  Brinkmann,  Harald  Clahsen,Richard Wiese,  and Steven Pinker. 1995. German inflection: The exception that proves the rule. *Cognitive psychology*, 29(3):189–256

# Citation

If you use this data in your own work, please cite the following reference:

```
@inproceedings{mccurdy_inflecting_2020,
	title = {Inflecting when there's no majority: {Limitations} of encoder-decoder neural networks as cognitive models for {German} plurals},
	abstract = {Can artificial neural networks learn to represent inflectional morphology and generalize to new words as human speakers do? 
	Kirov and Cotterell (2018) argue that the answer is yes: modern Encoder-Decoder (ED) architectures learn human-like behavior when inflecting English verbs, such as extending the regular past tense form /-(e)d/ to novel words. However, their work does not address the criticism raised by Marcus et al. (1995): that neural models may learn to extend not the \textit{regular}, but the \textit{most frequent} class --- and thus fail on tasks like German number inflection, where infrequent suffixes like \s\ can still be productively generalized.
	To investigate this question, we first collect a new dataset from German speakers (production and ratings of plural forms for novel nouns) that is designed to avoid sources of information unavailable to the ED model.
	The speaker data show high variability, and two suffixes evince `regular' behavior, appearing more often with phonologically atypical inputs. Encoder-decoder models do generalize the most frequently produced plural class, but do not show human-like variability or `regular' extension of these other plural markers. We conclude that modern neural models may still struggle with minority-class generalization.},
	booktitle = {Proceedings of the 58th {Conference} of the {Association} for {Computational} {Linguistics}},
	publisher = {Association for Computational Linguistics},
	author = {McCurdy, Kate and Goldwater, Sharon and Lopez, Adam},
	year = {2020}
}
```