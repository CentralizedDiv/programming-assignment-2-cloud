## Create volume
docker volume create arthurmelo-volume

## Build Image
docker build --tag arthurmelo/american-tweet-predictor .

## One-liner copy classifier to volume
docker run --rm -v $PWD:/source -v arthurmelo-volume:/app/model -w /source arthurmelo/american-tweet-predictor cp classifier.pickle /app/model

## Run Container, exposing port 5003
docker run -v arthurmelo-volume:/app/model -p 5003:5000 arthurmelo/american-tweet-predictor:latest
