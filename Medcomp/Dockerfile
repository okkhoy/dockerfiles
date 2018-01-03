# Start from Ubuntu 14.04 base image; 14.04 is supported till 2019; we have enough time!
# Well, because no Python2. 
# Well, because Long live inertia!!
FROM okkhoy/trusty-baseimage:baseimage-trusty

#trusty-baseimage          latest              6bcb8036e6ea        15 hours ago        270MB
#okkhoy/trusty-baseimage   baseimage-trusty

# Let us standardize and install Anaconda 4.3.31; in 4.4.0+ the default virtual environment activation
# has changed. For now, 4.3+ versions are supported, but any upgrade may prevent our existing code/environments
# from working. Hence stick to 4.3.31 (last 4.3 release before 4.4.0)
# Fix numpy, scipy, pandas and R to the latest available versions. 
# For Python 3, change the second line to 
# && curl -sSL https://repo.continuum.io/miniconda/Miniconda3-4.3.31-Linux-x86_64.sh -o /tmp/miniconda.sh \
# and the conda install -y python=2.7.14 to conda install -y python=3.6.3
RUN apt-get -qq update && apt-get -qq -y install curl bzip2 \
    && curl -sSL https://repo.continuum.io/miniconda/Miniconda2-4.3.31-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && bash /tmp/miniconda.sh -bfp /usr/local \
    && rm -rf /tmp/miniconda.sh \
    && conda install -y python=2.7.14 \
    && conda install -y numpy=1.13.3 scipy=1.0.0 scikit-learn=0.19.1 pandas=0.21.1 statsmodels=0.8.0 \
    && conda install -y r-essentials r=3.4.2 r-bcp rpy2 \
    && apt-get -qq -y remove curl bzip2 \
    && apt-get -qq -y autoremove \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* /var/log/dpkg.log \
    && conda clean --all --yes
    
ENV PATH /opt/conda/bin:$PATH

