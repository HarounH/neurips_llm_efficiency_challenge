```
conda activate onegpu
docker run --gpus all -p 8080:80 toy_submission

curl -X POST -H "Content-Type: application/json" -d '{"prompt": "The capital of france is "}' http://localhost:8080/process
```

# 2023/08/04
Aim: use LLaMa-2-chat model for inference

# 2023/08/03
1. install docker
2. ensure docker runs from wsl
3. run `docker build -t toy_submission .` from `toy-submission/` .... building can take a long time, so wait... seems pytorch is the slow thing, at 3.85GB to download and extract, it takes ~400s
4. Run service: `docker run --gpus all -p 8080:80 toy_submission`
5. query service: `curl -X POST -H "Content-Type: application/json" -d '{"prompt": "The capital of france is "}' http://localhost:8080/process`
