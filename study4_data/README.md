# Overview

The data contained in `study4_data.csv` were collected and reported by [McCurdy et al. (2022)](#Citation). The dataset contains German speaker responses to the task of inflecting novel nouns (developed by Marcus et al., 1995) into their plural form, and also predicting their gender. 

# Fields

The CSV file contains the following fields (with data type and short description):

- Subject properties, preceded by `S_`
	- `S_Participant_ID`
		- UUID
		- Anonymous identifier assigned to a unique participant
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
- Questions of interest to the study, based on the wug stimuli developed by Marcus et al. (1995), with answers A provided by participants.
	- `Q_List`
		- Text
		- Stimuli list seen by participant. Gender order presentation was counterbalanced across words in 3 lists.
	- `Q_Lemma`
		- Text
		- Novel noun from Marcus et al. (1995) stimuli. 
	- `A_Gender`
		- Text
		- Gender of the presented noun, selected by the participant. One of three categories:
			- Masculine (participant selected "Der")
			- Feminine (participant selected "Die")
			- Neuter (participant selected "Das")
	- `A_PL_Form`
		- Text
		- Plural form of M95 noun produced by subject. 
	- `A_PL_Suffix`
		- Text
		- Classification of `A_PL_Form` into one of 6 classes (ignoring umlaut):
			- e
			- en
			- er
			- zero
			- s
			- other
	- `A_PL_Suffix3`
		- Text
		- Classification of `A_PL_Form` into one of 3 classes, as used in paper analysis:
			- e
			- en
			- other


## Order of question presentation 

Note that the order of the fields in the data does not reflect the order of presentation in the study --- they have been rearranged to a "long" format for easier analysis. For questions with responses from subjects, the order of presentation was as follows:

- Study overview
- Study introduction and onboarding
	- Subjects were required to complete an introductory onboarding task of inflecting existing German words and assigning gender. Subjects were only able to proceed on producing the correct form. The onboarding words are listed below, with the correct gender and plural form.
		- Sache
			- Die 
			- Sachen
		- Kind
			- Das
			- Kinder
		- Schuh
			- Der
			- Schühe
		- Auto
			- Das
			- Autos
		- Apfel
			- Der
			- Äpfel
		- Pulli
			- Der
			- Pullis
		- Mutter
			- Die
			- Mütter
		- Hand
			- Die
			- Hände
		- Bär
			- Der
			- Bären
		- Maus
			- Die
			- Mäuse
		- Ohr
			- Das
			- Ohren
		- Jahr
			- Das
			- Jahre
- Production task
	- `Q_*`, `A_*`
- Background survey
	- `S_EN_Level`
	- `S_EN_Exposure`
	- `S_L1`
	- `S_L2s`
	- `S_Age`
	- `S_Regional_Background`

# References

Gary  F  Marcus,  Ursula  Brinkmann,  Harald  Clahsen,Richard Wiese,  and Steven Pinker. 1995. German inflection: The exception that proves the rule. *Cognitive psychology*, 29(3):189–256

# Citation

If you use this data in your own work, please cite the following reference:

```

```

