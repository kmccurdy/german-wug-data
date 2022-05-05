# Overview

The data contained in `study3_data.csv` were collected and reported by [McCurdy et al. (2020)](#Citation). The dataset contains German speaker responses to the task of inflecting novel nouns (developed by Marcus et al., 1995) into their plural form. The data contains both production and selection results for the same stimuli. 

Findings from these data, in combination with the data in [study 2](https://kmccurdy.github.io/assets/data/cmcl2020_study2_data.zip), were presented at AMLaP 2020. Please combine these data sets to reproduce the analysis in that presentation.

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
		- Text
		- Value of selected box on consent form
	- `S_Age`
		- Text
		- Subject reported age bracket, with the following levels:
			- Under 18
			- 18-24
			- 25-34
			- 45-54
			- 55-46
			- 65+
	- `S_EN_Level`
		- Text
		- Subject reported level of English proficiency, with the following levels (corresponding to CEFR designations):
			- No English proficiency
			- A1
			- A2
			- B1
			- B2
			- C1
			- C2
			- "Englisch ist eine Muttersprache von mir" | Native speaker of English
	- `S_EN_Exposure`
		- Text
		- Subject reported typical level of English exposure ("Roughly how often per week do you hear, speak, or read English?"):
			- "Weniger als eine Stunde pro Woche" | Less than an hour per week
			- "1-2 Stunden pro Woche" | 1-2 hours / week
			- "2-5 Stunden pro Woche" | 2-5 hours / week
			- "5-10 Stunden pro Woche" | 5-10 hours / week
			- "Mehr als 10 Stunden pro Woche" | 10+ hours / week
	- `S_L1`
		- Text
		- Subject reported native language 
	- `S_L2s`
		- Text
		- Subject reported second language proficiency other than English
	-`S_Regional_Background`
		- Text
		- Subject reported primary location where they grew up, to identify any regional or dialect-related trends; requested form PLZ, town/city, country code
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
	- `Q_List`
		- Integer
		- Stimuli list seen by participant. Gender was counterbalanced across words in 3 lists.
	- `Q_ID`
		- Text
		- Unique identifier for question (does not reflect question presentation order)
	- `Q_Response`
		- Text with task-dependent interpretation
		- Subject response to production or selection task. If production, the response is the plural form of the provided word. If selection, it is the form they selected.
	- `Q_Gender`
		- Text
		- Gender of the presented noun, indicated by the preceding definite article. One of three categories:
			- "der" masculine
			- "die" feminine
			- "das" neuter
	- `Q_Lemma`
		- Text
		- Novel noun from Marcus et al. (1995) stimuli. N.B. the nouns are in lowercase here for ease of data processing; when presented in the study, they were capitalized as is standard for German nouns (e.g. *Das Bral*).
	- `Q_Lemma_HasRhymes`
		- Logical (True, False)
		- True if Q_Lemma is in the "Rhymes" category (i.e. rhymes with existing German nouns), False if Q_Lemma is in the "Non-Rhymes" category
	- `Q_PL_Form`
		- Text
		- Plural form of M95 noun.
			- if `Q_Task` = "production": plural form produced by subject (lowercase)
			- if `Q_Task` = "selection": comma-separated set of plural forms presented to subject for selection
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
@inproceedings{mccurdy_modeling_2020,
	title = {Modeling grammatical gender and plural inflection in {German}},
	copyright = {All rights reserved},
	url = {https://amlap2020.github.io/a/261.pdf},
	booktitle = {Proceedings of the 26 {Architectures} and {Mechanisms} for {Language} {Processing} {Conference} ({AMLaP})},
	publisher = {Universität Potsdam},
	author = {McCurdy, Kate and Lopez, Adam and Goldwater, Sharon},
	month = sep,
	year = {2020}
}
```

