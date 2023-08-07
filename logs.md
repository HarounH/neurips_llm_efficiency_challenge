```
conda activate onegpu
docker run --gpus all -p 8080:80 toy_submission

curl -X POST -H "Content-Type: application/json" -d '{"prompt": "The capital of france is "}' http://localhost:8080/process
```

# 2023/08/06
1. Aim to have a more thorough baseline using larger run spec
2. Start understanding the different tasks and improving the ones you care about

# 2023/08/05
1. hugginface llama2...
2. `docker build -t toy_submission .` but now with llama2 model download
3. run service: `docker run --gpus all -p 8080:80 toy_submission` and notice that llama2 is loaded.
4. try a command: `curl -X POST -H "Content-Type: application/json" -d '{"prompt": "The capital of france is "}' http://localhost:8080/process`

**For eval**
1. make sure to install helm neurips client - it registers a neurips model locally which is compatible with toy submission.
2. Start the docker service using docker run in the background.
3. Kick off helm command like: `helm-run --conf-paths run_specs.conf --suite v1 --max-eval-instances 1000`
# 2023/08/04
Aim: use LLaMa-2-chat model for inference
1. add llama submodule, run download for 7b models
2. edit llama/.gitignore - gitignore from parent directory is weird.
3. Note that huggingface serves llama2 checkpoints - applied for that too.
4. However, I think that requires downloading llama2 again... which takes time, so TODO

# 2023/08/03
1. install docker
2. ensure docker runs from wsl
3. run `docker build -t toy_submission .` from `toy-submission/` .... building can take a long time, so wait... seems pytorch is the slow thing, at 3.85GB to download and extract, it takes ~400s
4. Run service: `docker run --gpus all -p 8080:80 toy_submission`
5. query service: `curl -X POST -H "Content-Type: application/json" -d '{"prompt": "The capital of france is "}' http://localhost:8080/process`
