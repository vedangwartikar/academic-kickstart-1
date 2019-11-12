---
title: "Using Generative Adversarial Networks for Secure Pseudorandom Number Generation"
authors: 
- Rajvardhan Oak
- admin
- Dhaval Gujar

date: "2019-11-11T00:00:00Z"
doi: "10.1145/3319535.3363265"

# Schedule page publish date (NOT publication's date).
publishDate: "2019-11-11T00:00:00Z"

# Publication type.
# Legend: 0 = Uncategorized; 1 = Conference paper; 2 = Journal article;
# 3 = Preprint / Working Paper; 4 = Report; 5 = Book; 6 = Book section;
# 7 = Thesis; 8 = Patent
publication_types: ["1"]

# Publication name and optional abbreviated publication name.
publication: In *ACM SIGSAC Conference on Computer and Communications Security*
publication_short: In *SIGSAC*

abstract: Generation of secure random numbers has always been a challenging issue in design and development of secure computer systems. Random numbers have important applications in the field of cryptography where the security of the scheme relies upon the random nature of the keys. It is not practically possible to achieve true randomness in a machine, and hence we rely upon Pseudo Random Number Generators (PRNGs) to produce near-true randomness. PRNGs use a mathematical function that relies upon a seed (a preset value required by the function to generate values) and it generates numbers which satisfy certain tests for randomness and appear to be random for a user having no knowledge of the generator function. These pseudorandom functions have their drawbacks due to them being derived from a mathematical function. To generate random numbers that can never be predicted by any observer, requires a causally non-deterministic process where events are not fully determined by prior states. Due to the physical impossibility of acquiring sufficient information to predict the outcome of such an event, its outcomes are guaranteed to be random to all. Various methods to generate pseudorandomness have been employed over the years which includes using mathematical functions, keyboard typing latency of the user, network latency, memory latency etc. as sources of generating random numbers. In this work, we propose a new way of generating pseudorandom numbers using generative adversarial networks. We demonstrate that a GAN can act as a Cryptographically Secure Pseudorandom Number Generator (CPRNG) passing 97% of National Institute of Standards and Technology (NIST) tests.

summary: We propose a new way of generating pseudorandom numbers using generative adversarial networks. We demonstrate that a GAN can act as a Cryptographically Secure Pseudorandom Number Generator (CPRNG) passing 97% of National Institute of Standards and Technology (NIST) tests.

tags:
- research
- ACM 
- security

featured: true

links:
- name: Publication Link
  url: https://dl.acm.org/citation.cfm?id=3363265
url_pdf: https://dl.acm.org/ft_gateway.cfm?id=3363265&ftid=2095403&dwn=1&CFID=171413636&CFTOKEN=dcf9cfde35ca9d7d-C4C7A804-E8A2-8FD3-A09D2CF807BE8BE9
url_code: ""
url_dataset: ""
url_poster: "https://github.com/chaitanyarahalkar/temporary-uploads/raw/master/Final-Poster.pdf"
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/pLCdAaMFLTE)'
  focal_point: ""
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: ""
---

