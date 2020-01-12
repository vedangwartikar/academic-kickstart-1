---
title: Content Addressed Peer-to-Peer File System for the Web with Blockchain-Based Metadata Integrity
event: Pune Institute of Computer Technology
event_url: http://pict.edu

location: Pune Institute of Computer Technology
address:
  street: Survey No. 27, Near, Trimurti Chowk, Bharati Vidyapeeth Campus, Dhankawadi 
  city: Pune
  country: India

summary: With the exponentially scaled World Wide Web, the standard HTTP protocol has started showing its limitations. With an increased amount of data duplication \& accidental deletion of files on the Internet, the P2P file system called IPFS completely changes the way files are stored. IPFS is a file storage protocol allowing files to be stored on decentralized systems. In the HTTP client-server protocol, files are downloaded  has from a single source. With files stored on a decentralized network, IPFS allows packet retrieval from multiple sources, simultaneously saving considerable bandwidth. IPFS uses a content-addressed block storage model with content-addressed hyperlinks. Large amounts of data can is addressable with IPFS with the immutable and permanent IPFS links with meta-data stored as Blockchain transactions. This timestamps and secures the data, instead of having to put it on the chain itself. Our paper proposes a model to use the decentralized file storage system of IPFS, and the integrity preservation properties of the Blockchain, to store and distribute data on the Web.

# Talk start and end times.
#   End time can optionally be hidden by prefixing the line with `#`.
date: "2018-03-27T11:00:00Z"
date_end: ""
all_day: false

# Schedule page publish date (NOT talk date).
publishDate: ""

authors: ["Chaitanya Rahalkar"]
tags: ["http","peer-to-peer","blockchain","file system"]

# Is this a featured talk? (true/false)
featured: false

image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/bzdhc5b3Bxs)'
  focal_point: Right

links: 
url_code: ""
url_pdf: ""
url_slides: "https://github.com/chaitanyarahalkar/temporary-uploads/raw/master/Seminar.pdf"
url_video: ""

# Markdown Slides (optional).
#   Associate this talk with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []

# Enable math on this page?
math: true
---

With the exponentially scaled World Wide Web, the standard HTTP protocol has started showing its limitations. With an increased amount of data duplication & accidental deletion of files on the Internet, the P2P file system called IPFS completely changes the way files are stored. IPFS is a file storage protocol allowing files to be stored on decentralized systems. In the HTTP client-server protocol, files are downloaded  has from a single source. With files stored on a decentralized network, IPFS allows packet retrieval from multiple sources, simultaneously saving considerable bandwidth. IPFS uses a content-addressed block storage model with content-addressed hyperlinks. Large amounts of data can is addressable with IPFS with the immutable and permanent IPFS links with meta-data stored as Blockchain transactions. This timestamps and secures the data, instead of having to put it on the chain itself. Our paper proposes a model to use the decentralized file storage system of IPFS, and the integrity preservation properties of the Blockchain, to store and distribute data on the Web.



With the ever-expanding World Wide Web, the data generated on the web has grown vastly. The amount of data generated daily is at a staggering 2.5 quintillion bytes. This pace is gaining constant momentum due to the inclusion of new IoT devices every day. Sensory data produced by IoT devices get bulkier as modern devices are added to the Internet. To counter the problem of data handling, many distributed file systems were introduced. The popular ones being Napster, BitTorrent, KaZaA, supporting millions of distributed users. Among all of them, HTTP - one of the oldest protocols on the Internet is the biggest distributed file system, when coupled with browsers allowing users to share files globally. With the increase in the scalability of the World Wide Web, the reliability of  HTTP began to degrade. Keeping track of terabytes of data and moving these files over the Web is a difficult task. Several other protocols were introduced to tackle the problem of scalability and decentralization with an intention of replacing the well-established reign of HTTP. 
The other problem with HTTP is security and data integrity. As a countermeasure, the inclusion of Blockchain technology was introduced. Blockchain technology cannot be used to store the entire data due to its distributed ledger protocol. This protocol states that every node in the Blockchain must preserve a copy of the data, on the chain. Hence, storing petabytes of data on the Blockchain is infeasible. This model proposes to store only the file metadata, summarizing necessary information about data, on the Blockchain. This data, being in bytes for a single file, reduces the overall size of the ledger.



Get a copy of the talk slides [here](https://github.com/chaitanyarahalkar/temporary-uploads/raw/master/Seminar.pdf)
