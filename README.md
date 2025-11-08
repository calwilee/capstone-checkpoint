## Uncertainty Quantification for LLMs

This respository contains code from the repo given by the paper Decomposing Uncertainty for Large Language Models
through Input Clarification Ensembling. I have written code to parse outputs, and edited model prompts, as well as run experiments using Llama3.1:8b instead of gpt3.5. 

Currenrly, code is being uploaded to github, taking a while. This may be the reason the repo is empty besides this readme for now. 

### Requirements

The dependency packages can be found in `requirements.txt` file. One can use `pip install -r requirements.txt` to configure the environment. We use python 3.8 to run the experiments.


### Pipeline 
This code pipeline was used for testing on multiple choice and free response data:
python tools/generate_clarification.py --dataset_name ambig_inst --output_path logs/clarification/ambig_inst.json --sample --sample_n 2

python forward.py --dataset_name ambig_inst --clarification_path logs/clarification/ambig_inst.json --output_path logs/forward/ambig_inst_forward.json

python evaluate_uq_ambiginst.py --log_path logs/forward/ambig_inst_forward.json --output_path logs/uq_eval/ambig_inst.json --answer_key clarified_all_ans