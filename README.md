# Esolai: A ESL-based AI teacher
This is the repo for the Miami Hackathon's Team #76's Esolai project, which aims to build and use an instruction-following model. This repo contains:
- The 52K data used for fine-tuning the model.
- The code for generating the data
- The code for fine-tuning the model

## Overview
The current Esolai model is fine-tuned on a 52K instruction-following data generated by the techniques in the [Self-Instruct](https://github.com/yizhongw/self-instruct) repo, with some modifications that we discuss in the next section.

Esolai is still under development, and there are many limitationts that have to be addressed. Importantly, we have not yet fine-tuned the model to be safe and harmless.

Our initial release contains the data generation procedure, dataset, and training recipe.

# Data Release
[esolai_data.json](URL) contains the 52K instruction-following data we used for fine-tuning the model. This JSON file is a list of dictionaries, each dictionary contains the following fields:

- `instruction`: `str`, describes the task the model should perform. All the instructions are unique.
- `input`: `str`, optional context or input for the task. For example, when the instruction is "Identify the main idea of this sentence", the input would be the sentence.
- `output`: `str`, the answer to the isntruction.

# Data Generation Process
We built on the data generation process from [self-instruct](https://github.com/yizhongw/self-instruct) and made the following modifications:

- We used `gpt-3.5-turbo` to generate the instruction data instead of `davinci`
- We used Stanford's Alpaca method to write a new prompt and to generate instructions with [prompt.txt](u).

This produced an instruction-following dataset with 52K examples which was obtained at a much lower cost than Stanford's Alpaca (less than $300) based off our seeds
([esolai_seeds.json](https://github.com/tiagid/ESOL-AI/blob/main/esolai_seeds.json)), in which the instructions were based on the curriculum that ESL students levels 1-5 must learn, which is based around the verbs of:
For the seeds, the root verb of the instructions are:

- Match
- Identify
- Evaluate
- Write
- Answer
- Summarize
- Defend
- Argue

These [seeds](https://github.com/tiagid/ESOL-AI/blob/main/esolai_seeds.json) were handwritten by ourselves to ensure that the 52K instructions generated were as close as possible to ESL curriculum.
