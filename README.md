# Docker file for cami2 challenge.

# Introduction 
to build docker images:
cat CAMI_2019/DOCKER_CAMI2019 | docker build  -t cami2019 -

## Marine dataset assembly: \
docker run -v /path/to/raw/reads/:/rawdata/ \
-v /path/to/store/longreads/:/long_reads/ \
-v /path/to/store/deinterleaved/shortreads/:/short_reads/ \
-v /path/to/output/:/outdata/ \
-i -t cami2019 python /SCRIPT/start_pipeline.py -d marine -co no

## Marine dataset co-assembly:
docker run -v /path/to/raw/reads/:/rawdata/ \
-v /path/to/store/longreads/:/long_reads/ \
-v /path/to/store/deinterleaved/shortreads/:/short_reads/ \
-v /path/to/output/:/outdata/ \
-i -t cami2019 python /SCRIPT/start_pipeline.py -d marine -co yes

## Strain madness dataset assembly:
docker run -v /path/to/raw/reads/:/rawdata/ \
-v /path/to/store/longreads/:/long_reads/ \
-v /path/to/store/deinterleaved/shortreads/:/short_reads/ \
-v /path/to/output/:/outdata/ \
-v /path/to/kraken_db/:/kraken_db/ \
-i -t cami2019 python /SCRIPT/start_pipeline.py -d strain_madness -co no

## Strain madness dataset co-assembly:
docker run -v /path/to/raw/reads/:/rawdata/ \
-v /path/to/store/longreads/:/long_reads/ \
-v /path/to/store/deinterleaved/shortreads/:/short_reads/ \
-v /path/to/output/:/outdata/ \
-i -t cami2019 python /SCRIPT/start_pipeline.py -d strain_madness -co yes

# NOTE
/path/to/store/longreads/ \
/path/to/store/shortreads/ \
path/to/output/ \
should be created and emptied before running the pipeline
