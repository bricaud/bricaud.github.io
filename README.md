## Bio

I am a researcher at EPFL, Lausanne Switzerland. My research is at the intersection between Data Science, Network Science, Machine Learning and Signal Processing. 

My main research topics are:
 * [Graph signal processing](#graph-signal-processing)
 * [Exploration of large graphs](#exploration-of-large-graphs)
 * [Graphs in biology](#graphs-in-biology)
 * [Machine learning in audio and explainable AI](#machine-learning-in-audio-and-explainable-ai)
 * [Sparsity in data](#sparsity-in-data)


## Graph signal processing
![Graph Signal Processing]({{site.baseurl}}/assets/img/GSPimage.png)
Since I joined the LTS2 lab at EPFL in 2012, I have been working on graph structured data. The main idea is to design new methods enabling the analysis of phenomena occurring within networks. With the explosion of data, these structures arise in many different fields of application (engineering, biology, physics...). In graph signal processing and graph machine learning,  we distinguish two sources of information we combine together: 1) the graph and 2) the data associated to the graph nodes or edges. The graph is the structure or space and the data are the signal or feature vectors. Our first effort was to show how standard data analysis methods in 1D or 2D could be generalized to this exotic graph space. We showed the generalization of key signal processing methods and concepts to the graph setting such as the Fourier transform, the concept of frequency and sparse representation [GSP1], the windowed Fourier transform [GSP2], dynamic analysis on graphs [GSP3] and the concept of uncertainty [GSP4]. I wrote recently a review paper about these methods [GSP5]. 

[[GSP1](https://documents.epfl.ch/users/s/sh/shuman/www/Papers/Conference/Shuman_et_al_SSP_2012.pdf)] David I Shuman, Benjamin Ricaud, and Pierre Vandergheynst. A windowed graph fourier transform. In Statistical Signal Processing Workshop (SSP), 2012 IEEE, pages 133–136. Ieee, 2012.

[[GSP2](https://www.sciencedirect.com/science/article/pii/S1063520315000214)] Shuman, D. I., Ricaud, B., & Vandergheynst, P. (2016). Vertex-frequency analysis on graphs. Applied and Computational Harmonic Analysis, 40(2), 260-291.

[[GSP3](https://arxiv.org/abs/1705.02307)] Francesco Grassi, Andreas Loukas, Nathanael Perraudin, and Benjamin Ricaud. A time-vertex signal processing framework: Scalable processing and meaningful representations for time-series on graphs. IEEE Transactions on Signal Processing, 66(3):817–829, 2018.

[[GSP4](https://doi.org/10.1017/ATSIP.2018.2)
] PERRAUDIN, Nathanael, RICAUD, Benjamin, SHUMAN, David I., et al. Global and local uncertainty principles for signals on graphs. APSIPA Transactions on Signal and Information Processing, 2018, vol. 7. 

[[GSP5](https://www.sciencedirect.com/science/article/pii/S1631070519301094)] Benjamin Ricaud, Pierre Borgnat, Nicolas Tremblay, Paulo Gonçalves, and Pierre Vandergheynst. Fourier could be a data scientist: From graph fourier transform to signal processing on graphs. Comptes Rendus Physique, 20(5):474 – 488, 2019.

## Exploration of Large graphs
![Large Twitter graph]({{site.baseurl}}/assets/img/higgs_community_small.jpg)
With the increasing size of networks, methods based on linear algebra, such as graph signal processing, or machine learning may not be as efficient. New approaches are needed, involving scalable processes. We have developed several such approaches. One direction is the analysis of abnormal activity (or peak of activity) in the large network of Wikipedia hyperlinks. The number of visits per hour is recorded for each page by Wikimedia and made freely available. Analyzing the activity inside the network reveals the human curiosity and behavior related to important events and news [W1,W2,W3]. A presentation of the findings is available on a blog post of my co-author [V. Miz](https://miz.space). An emblematic example of large scale network is the social network. I am involved in a project with a Swiss media consortium [IMI](https://www.media-initiative.ch/) to analyze and track controversies and fake news in social networks. In addition to the size of the network, the limited access to the social platform via an API is a challenge. We have proposed an innovative network exploration principle to unlock the exploration of social networks [SP4].

[[W1](https://dl.acm.org/doi/pdf/10.1145/3308558.3313541)] Miz, V., Ricaud, B., Benzi, K., & Vandergheynst, P. (2019, May). Anomaly detection in the dynamics of web and social networks using associative memory. In The World Wide Web Conference (pp. 1290-1299).

[[W2](https://dl.acm.org/doi/pdf/10.1145/3308560.3316757)] Aspert, N., Miz, V., Ricaud, B., & Vandergheynst, P. (2019, May). A graph-structured dataset for Wikipedia research. In Companion Proceedings of The 2019 World Wide Web Conference (pp. 1188-1193).

[[W3](https://dl.acm.org/doi/pdf/10.1145/3366424.3383567)] Miz, V., Hanna, J., Aspert, N., Ricaud, B., & Vandergheynst, P. (2020, April). What is Trending on Wikipedia? Capturing Trends and Language Biases Across Wikipedia Editions. In Companion Proceedings of the Web Conference 2020 (pp. 794-801).

[[SP4](https://www.mdpi.com/1999-4893/13/11/275)] Benjamin Ricaud, Nicolas Aspert, and Volodymyr Miz. Spikyball sampling: Exploring large networks via an inhomogeneous filtered diffusion. Algorithms, 13(11):275, 2020.

## Graphs in biology
![EEG network scheme]({{site.baseurl}}/assets/img/brainfigure.png)
I have worked on medical applications of graph signal processing, to understand the dynamical processes inside the brain (and its network of interconnected brain regions). In [BIO2] the network was the network of EEG sensors where their signals evolve over time as the patients are asked to complete a task. We showed that combining the temporal signals with a sensor network structure could reveal hidden correlations and help distinguish signs of early Alzheimer desease. In [BIO1] the combination of the graph of connected brain regions with the dynamic activity of these regions recorded from MRI scans improved the extraction of activity patterns such as the resting state network as well as new patterns.

[[BIO1](https://www.sciencedirect.com/science/article/abs/pii/S105381191730304X)] Alessandra Griffa, Benjamin Ricaud, Kirell Benzi, Xavier Bresson, Alessandro Daducci, Pierre Vandergheynst, Jean-Philippe Thiran, and Patric Hagmann. Transient networks of spatio-temporal connectivity map communication pathways in brain functional systems. NeuroImage, 155:490–502, 2017.

[[BIO2](https://www.nature.com/articles/srep42013)] Keith Smith, Benjamin Ricaud, Nauman Shahid, Stephen Rhodes, John M Starr, Augustin Ibáñez, Mario A Parra, Javier Escudero, and Pierre Vandergheynst. Locating temporal functional dynamics of visual short-term memory binding using graph modular dirichlet energy. Nature Scientific Reports, 7:42013, 2017.

## Machine learning in audio and explainable AI
I used to work on audio applications before coming to EPFL, as an aplication to signal processing. I studied sparse representation of audio and acoustic signals (time-frequency analysis). I recently came back to this topic with machine learning, helped by some signal processing expertise. We have designed learnable filter banks inside a neural net layer [ML2]. These are convolutional layers with parameterized kernels, where the parameters are the cut-off frequencies and shape of band pass filters. These kernels can be interpreted and the learning is faster as there a less weights to learn.
In a collaboration with Logitech, we investigate state-of-the-art AI in audio signal processing (speech and music) and focus on reducing the size of the deep networks in order to make them faster to train and more convenient for real-world audio applications [ML1,ML3]. 

[ML1] Berkay Inan, Milos Cernak, Helmut Grabner, Helena Peic Tukuljac, Rodrigo CG Pena, and Benjamin Ricaud. Evaluating audiovisual source separation in the context of video conferencing. In INTER-SPEECH 2019, pages 4579–4583. ISCA, 2019.

[[ML2](https://openreview.net/pdf?id=HyewT1BKvr)] Helena Peic Tukuljac, Sparse and Parametric Modeling with Applications to Acoustics and Audio, Phd Thesis, EPFL, 2020. Article submitted: Helena Peic Tukuljac, Benjamin Ricaud, Nicolas Aspert, Pierre Vandergheynst, SpectroBank: A filter-bank convolutional layer for CNN-based audio applications.

[ML3] Alexandru Mocanu, Benjamin Ricaud, Milos Cernak, Fast accuracy estimation of deep learning based multi-class musical source separation, submitted to ICASSP, 2020.

## Sparsity in data
I have worked on theoretical concepts in signal processing and graph signal processing such as sparsity and sparse signal representations [SP1, SP2, SP3].

[SP1] Benjamin Ricaud and Bruno Torrésani. Refined support and entropic uncertainty inequalities. IEEE Transactions on Information Theory, 59(7):4272–4279, 2013.

[SP2] Benjamin Ricaud and Bruno Torrésani. A survey of uncertainty principles and some signal processing applications. Advances in Computational Mathematics, 40(3):629–650, 2014.

[SP3] Benjamin Ricaud, David I Shuman, and Pierre Vandergheynst. On the sparsity of wavelet coefficients for signals on graphs. In Wavelets and Sparsity XV, volume 8858, page 88581L. International Society for Optics and Photonics, 2013.