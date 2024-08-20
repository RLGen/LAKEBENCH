<div>
    <h1>Starmie</h1>
</div>


![The overall architecture of Starmie](starmie_overall.jpg)
<br>

<h2>Folder Structure</h2>

```
.
├─── pretrain.py             # Pretrain
├─── index.py                # Index the columns of tables
├─── query.py                # Get the union results                         
├─── hnsw_search.py     
└─── starmie.md
```

<br>

<h2>Training Steps</h2>

**Step1: Check your environment**

You need to properly install nvidia driver first. To use GPU in a docker container You also need to install nvidia-docker2 ([Installation Guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html#docker)). Then, Please check your CUDA version via `nvidia-smi`

**Step2: Pretrain**

Here are some parameters:

> -- task [Choose task, str] [opendata, opendata_large, webtable, webtable_large]

```sh
python pretrain.py --task webtable
```

**Step3: Indexing**

Here are some parameters:

> --benchmark [Choose benchmark, str] [opendata, opendata_large, webtable, webtable_large]

```sh
python index.py --benchmark webtable
```

**Step4: Querying**

> --benchmark [Choose benchmark, str] [opendata, opendata_large, webtable, webtable_large]
>
> --K [Choose top-*k* ,int] [5~60]
>
> --threshold [Choose threshold, float] [0.5~1.0]
>
> --N [Choose N, int] [4, 10, 16, 25, 50]

```sh
python query.py --benchmark webtable --K 5 --N 10 --threshold 0.7
```