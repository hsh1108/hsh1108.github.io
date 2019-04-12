---
layout: post
title: Caffe installation
---


1.
본인 우분투 서버 버전은 18.04.2여서 공식사이트의 Installing pre-compiled Caffe를 먼저 시도했다.
$ sudo apt install caffe-cuda
시도했으나 ModuleNotFoundError: No module named 'caffe'로 실패...


2.
한참을 찾다가 모르겠어서 결국  Installing Caffe from source시도
Prerequisites 관련해서 먼저 해야할게 많다..
- CUDA 설치
버전 7이상이여야 한다.
> $ nvcc --version
로 확인 결과 본인 서버는 버전 10.0으로 설치되어있다. pass

- BLAS 설치
> $ sudo apt-get install libatlas-base-dev

- General dependencies(boost, protobuf, glog, glasgs, hdf5)
뭐하는 것들인지는 모르겠으나...
> $ sudo apt-get install libprotobuf-dev libleveldb-dev libsnappy-dev libopencv-dev libhdf5-serial-dev protobuf-compiler
> $ sudo apt-get install --no-install-recommends libboost-all-dev

- Opencv 설치
버전 2.4 이상이여아한다.
> $ pkg-config --modversion opencv
로 확인 결과 본인 서버는 버전 3.2.0으로 설치되어있다. pass
- MATLAB interface
MATLAB interface를 compile 하려면 설치해야하는데 optional이므로 나는 안했다.

3.
Compilation
> $ git clone https://github.com/BVLC/caffe.git
> $ cd caffe
caffe디렉토리에 있는 Makefile.config를 내 서버의 환경에 맞게 수정해야 한다.
> $ cp Makefile.config.example Makefile.config
https://github.com/BVLC/caffe/pull/1667 를 참조해서 자신의 환경에 맞게 수정하라는데..
내가 주석제거한 부분은 다음과 같다.
> USE_CUDNN :=1
> OPENCV_VERSION := 3
> CUDA_DIR

<dl>
  <dt>Ornare</dt>
  <dd>Cras vel nisi condimentum, hendrerit lacus sed, scelerisque ipsum.</dd>
  <dt>Convallis</dt>
  <dd>In lorem erat, sollicitudin varius posuere id, molestie ac eros</dd>
</dl>

Proin at libero id lorem fermentum elementum quis eget est.

1. Nam bibendum turpis massa, at accumsan justo fermentum ac.
2. Nulla non nulla ut ante condimentum mattis vel at lectus.
3. Etiam eget tortor tincidunt, iaculis ligula a, tristique massa. Fusce sed congue lorem, interdum sodales nisl.

Etiam consequat euismod ornare. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Nulla pellentesque ipsum vulputate, pellentesque nisl vitae, lacinia sem. Praesent auctor felis et odio ultrices, nec tempor elit lobortis. Etiam ornare massa non risus luctus, id iaculis lacus egestas. Pellentesque massa dolor, mattis id lobortis eget, tristique vitae est.

---

Nam vulputate leo vitae libero vehicula, id tincidunt velit malesuada. In vel ornare nisi, id semper turpis. Vivamus erat elit, venenatis quis dui at, convallis suscipit sapien. Nunc in nisi scelerisque, aliquam mauris porttitor, facilisis ligula. Vestibulum cursus erat ac turpis bibendum, id pulvinar dolor dapibus. Proin vitae justo et velit imperdiet ultrices id id odio. Cras adipiscing ante vel mauris lobortis rutrum. Aenean eu felis est. In lacinia porttitor risus non sagittis.

<div class="highlight"><pre><span class="k">class</span> <span class="nc">Greeter</span>
  <span class="k">def</span> <span class="nf">initialize</span><span class="p">(</span><span class="n">message</span><span class="p">)</span>
    <span class="vi">@message</span> <span class="o">=</span> <span class="n">message</span>
  <span class="k">end</span>

<span class="k">def</span> <span class="nf">greet</span>
<span class="nb">puts</span> <span class="n">message</span>
<span class="k">end</span>
<span class="k">end</span>

<span class="n">john</span> <span class="o">=</span> <span class="no">Greeter</span><span class="o">.</span><span class="n">new</span> <span class="s1">&#39;Hello, World&#39;</span>

<span class="n">john</span><span class="o">.</span><span class="n">greet</span>

</pre></div>

Sed imperdiet interdum ultrices. Phasellus iaculis porttitor lorem nec scelerisque. Suspendisse eros urna, adipiscing vel luctus at, feugiat sit amet arcu. Aliquam porttitor ut urna pellentesque sagittis. Donec pellentesque venenatis diam sit amet cursus. Etiam luctus, metus quis gravida fermentum, tortor arcu consequat metus, eget viverra augue risus ac dui. Fusce faucibus scelerisque quam eu sagittis. Sed sit amet sapien non augue lobortis adipiscing. Sed sagittis at lectus eu tempus. Nulla non nulla ut ante condimentum mattis vel at lectus. Nulla ultricies dui et urna semper ultrices. Sed neque ante, dictum in dignissim luctus, facilisis ornare odio. Aenean tempor ultrices magna non pharetra. Curabitur vulputate nec est aliquet suscipit. Etiam ipsum sapien, dictum quis tristique vel, pretium at elit.
