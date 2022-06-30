---
title:  "How to setting GPU Driver and Cuda"
date:   2022-06-30 16:56:23
categories: [SetupGPU]
tags: [GPUDRIVER]
---

# Device Check

## GPU CHECK

    update-pciids

- gpu update

    lspci | grep -i nvidia

- check gpu about model name

## Driver Check

    nvidia-smi

- check driver 

    apt —installed list | grep nvidia-driver

- nvidia-smi가 확인되지 않거나, 그래픽 드라이버에 문제가 없다고 생각되면 위의 명령어로 드라이버가 제대로 설치 되었는지 확인한다.
- 확인 후, 드라이버가 잘못 설치되었음이 확인되면 삭제 후 재 설치 한다.
- 설치된 드라이버가 확인 되지 않으면 재 설치 한다.

## CUDA CHECK

    nvcc —version


- CUDA VERSION CHECK

    ls /usr/local/cuda/lib64

    ls /usr/local/cuda/lib64


- 직접적으로 확인하고 싶다면, 기본적으로 cuda가 설치되는 위의 폴더에 가서 확인한다.
- 만약 폴더 안에 라이브러리들 (libcudart.{version})이 확인되고,


    ls /usr/local


- 위의 명령어 출력에 cuda-{version} 폴더가 확인되면 아래와 같이 환경변수를 확인해준다.

    vi ~/.bashrc

- bashrc 스크립트에 아래와 같이 내용 추가


    export PATH=/usr/local/cuda-{version}/bin:$PATH
    export LD_LIBRARY_PATH=/usr/local/cuda-{version}/lib64:$LD_LIBRARY_PATH


![Alt text](D:\ada\git\blog\eunseo-engineer.github.io\images\cuda_path_in_bashrc.png)


- 위와 같이 맨 아랫줄에 cuda-{version}의 경로를 환경변수에 적용 시켜준다. (마지막줄은 추가하지 않아도 된다.)


    source ~/.bashrc

- 저장(ESC + : wq!) 후, 위의 명령어로 저장한다.
- 그 다음 nvcc —version으로 cuda를 확인한다.







<!-- ---
title:  "Welcome to Eunseo's Blog!"
date:   2016-01-08 15:04:23
categories: [github blog]
tags: [jekyll]
---
You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve --watch`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

``` ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```

Check out the [Jekyll docs][jekyll] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll’s dedicated Help repository][jekyll-help].

[jekyll]:      http://jekyllrb.com
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-help]: https://github.com/jekyll/jekyll-help -->
