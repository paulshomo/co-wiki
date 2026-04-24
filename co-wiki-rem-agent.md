# The Co-Wiki and REM Agent:  
## A Legible Memory Architecture for the Second Brain

There’s no way the current LLM chat interface ends up a dominant design. Its inconceivable chat threads piled into project containers will still be housing human-AI discussions in 5 years. 

I’d say the same of flat-RAG architectures, built without a prominent warm storage layer. I have no issue with vector DBs as cold storage. Yet a *legible* warm storage is actually the backbone of the "second brain"  -- this era’s implied promise of delegating our thinking to a personal AI. A second brain that *always has our top-of-mind, and adjacent information, both stored in its extended memory and easily accessible by humans.* 

## Confronting Chat Hell
Chat hell is when knowledge evaporates from LLM chats without a clear harvest workflow. It’s when project containers fail to corral spaghetti piles of threads \-- each with crown jewels and referenceable information hiding under mountains of slop. Chat hell is the lack of workflows for managing quantity and redundancy. It’s zero editing, merging, or versioning. 

The chat workflow did successfully invite humans to converse with AI. Yet long term, the chat interface may be the worst of all content design patterns.

## Fixing Flat-RAG
The Co-Wiki doesn't replace RAG cold storage — it provides the warm layer for LLM memory, designed for human-agent co-authorship. It makes RAG dramatically more effective by pre-processing semantic boundaries and knowledge relationships before they reach the vector index.

RAG architectures without such legible memory layers have issues: 
1. They’re not human readable, but black holes of storage.
2. RAG chunking algorithms don’t make sense, despite all the engineering efforts behind them. RAG must move data in chunks, but it always seems to create them on artificial boundaries. Never with reference to the underlying content. 

As an example, RAG often defaults to a single chunking approach \-- often 512-token slices. Not ideal across data as heterogeneous as books and social media posts. 

The Co-Wiki addresses each of these failures directly.

## The Co-Wiki: a Storage Philosophy for the Second Brain   
The Co-Wiki was inspired by Andrej Karpathy’s “LLM Knowledge Base.” Karpathy introduced a wiki workspace accessed by agentic processes for maintenance, health checks, and to find new connections and introduce backlinks. 

Yet Karpathy is an Obsidian user and summarized his design as, “Obsidian is the IDE, the LLM is the programmer, the wiki is the codebase.” His is not actually a full wiki design with wiki benefits, but as he called it, a "collection of scripts."

Karpathy didn’t endeavor to break out of chat hell and isn’t trying to completely reimagine warm storage, but the Co-Wiki does. The wiki is *the* dominant design for all-in-one reading, navigation, editing, approval, and versioning workflows. 

Highly underrated is the wiki’s organic knowledge chunking.

The Co-Wiki proposed here is a flat and brutally simple architecture. The wiki is a legible memory layer. *The wiki is warm storage.* It dreams of dramatically reducing vector DB reads, but its priority lies in presenting natural language and reducing human cognitive load.   

![Co-Wiki Memory Stack](https://raw.githubusercontent.com/paulshomo/co-wiki/main/co_wiki_memory_stack_dark.svg)

## REM Agent   
Wikis have a reputation for high maintenance. The Wiki Gardening Problem \- bloat, stale pages, and the need to fix or create brand new backlinks. In the Co-Wiki, these represent an opportunity to design the REM Agent.

A REM Agent must implement pruning and decay to clean out gunk, eliminate redundancy, irrelevance, and age out content during sleep. REM also needs a dreaming algo to locate new connections and create backlinks, and even add new content. This is something Karpathy's design had as well.

The REM Agent’s pruning, decay and dreaming algo are intimidating to build. This doc doesn’t design them, only provides an architecture to start on. 

Personally I’d biomimic known cognitive processes during REM sleep. Cognitive Psychology teaches us: 
* The brain values content by Novelty, Emotional Salience, and Contextual Association (number of backlinks). These imply memories, or in our case Co-Wiki pages, should have staying power. 
* Decay Theory might offer a fading algo.
* Page access is analogous to the cognitive concept called Repetition. 
* The user repeating information for better retainment is called Rehearsal. 
* What about the Motivated Forgetting of pages that cause cognitive dissonance? Deprecate, redirect, or keep, LOL.

The first Co-Wiki deployment is a serious experiment in human memory. How large is an individual's top-of-mind and adjacent knowledge when externalized? We’ve never measured it. 

## LLM Integration Without APIs or Infrastructure Deployment  
The best part is it may require zero infrastructure or APIs to connect your LLM-chatbot and agents to the Co-Wiki.

I’ll leave it to the reader to pick an open source wiki codebase to start from. Relevant research is highlighted below, please verify\!

Let's consider popular wiki codebases and their backends. Outside MediaWiki (Wikipedia), DokuWiki is the next most deployed and targets private, internal, and personal deployments. TiddlyWiki is another.

Coincidentally, Andrej Karpathy’s choice of Obsidian Vault resembles DokuWiki’s back end. Each keep pages as flat files (\*.txt or \*.md), stored in directory structures with categorically named folders. Reading the folder names builds the namespace. 

Consider how profound an LLM is integrated with such a flat file backend. The LLM can be directly connected through the filesystem: aka “ls” command and reading file content. *This means no API or infrastructure deployment is required between the agent/LLM and warm storage!*

Don't you have to code an integration between the LLM with the wiki's backend files? *No!!!* Prompting an LLM to navigate the directories and read files does the trick. LLM's literally understand the files and build a full knowledge graph nearly for free, with minimal tokens. Converting the DokuWiki's .meta file format into human-readable companion files would only be required as a lightweight preprocessing step that an LLM could handle itself. 

This is what’s meant by API-less and without infrastructure deployment.

Here is the Co-Wiki design philosophy:

### Editing and co-authorship is everything  
How exactly does the Co-Wiki work from the user perspective?

Like today's LLM interactions, the chat session is the backbone of the Co-Wiki. What's different here is that at the end of a chat session, valuable information is harvested into related Co-Wiki articles. 

The human user and multiple agentic tasks can edit and generate content. Unlike the serial LLM chat, a major workflow is *human editing of any past Co-Wiki content: chats, saved data, etc., everything can be edited*. 

LLMs could aid humans in Co-Wiki article writing, commits, merges, or splits. Auditing and versioning is paramount considering the privacy and security implications.

### Backlinks and categories become first class citizens  
Backlinks deeply parallel the mind’s “cognitive associations,” connecting relevant knowledge. It’s no accident academic citations and Google’s PageRank became classics. Wikis, like Wikipedia, also organize human knowledge with navigable backlinks and categorical navigation. 

Co-authorship means both Co-Wiki agents and humans naturally organize content into pages, backlinks and categorical taxonomies.

### Let human cognition and social consensus chunk data   
Humans naturally create and organize knowledge for reading, and in the case of article size, that means creating read-sized chunks. It also means letting the user group articles in comprehensible categories. 

Why set chunk boundaries at token counts or paragraph breaks, when it can be set as an idea achieves sufficient closure. The Co-Wiki literally chunks content at the edge of human cognition.

### Warm storage is legible and human optimized 
Legible memory is not an LLM optimization, don’t be confused. The Co-Wiki is doubling as warm storage and a browsable presentation layer. In the grand scheme of formatting, a legible storage format is not optimized from a token usage or storage perspective, but would scale for personal usage.

Legible memory is analogous to human declarative memory, which contains accessible language that’s consciously and explicitly available. Unlike the vector DB, but like our own declarative memory, the user can directly read from the Co-Wiki. 

The Co-Wiki is a flat and brutally simple architecture.

### An organic knowledge graph has beaten straight RAG semantic searches  
This knowledge graph approach allows LLMs to not only know available pages, but dynamically load context like the human mind’s Spreading Activation process. Cues activate an article, backlinks traverse and spread to connected nodes, with the most strongly connected and recently activated pages surfacing first. 

The Co-Wiki’s biomimicry is not unique in storage schemes, see the MIRIX memory research framework. A-Mem also leverages interconnected knowledge networks through dynamic indexing, linking, and contextual descriptions. Yet neither A-Mem nor MIRIX explicitly store legible language.

One Co-Wiki implementation by [copyleftdev](https://github.com/copyleftdev) was built from a wiki codebase storing flat files of a similar structure to DokuWiki or Obsidian Vault. In testing it was not only extremely fast but [outperformed](https://github.com/copyleftdev/cowiki-rs/blob/main/PROOF.md) traditional searches of the vector DB index.

## Problem of Agent Read/Write Asymmetry   
Wiki co-authorship typically implements an optimistic concurrency model. Anyone can edit and conflicts are resolved afterwards through diffing and merging. Thus there is no preventative locking. 

While reading wiki backend files from the filesystem is fast, cheap, API-less, and has no concurrency issues, writing is more complex.

Some operations would need concurrency protections to be built. Think atomic operations like renaming a page, updating backlinks across multiple files, deprecating a concept that's referenced in twelve places. 

[Also see Frequently Asked Questions (FAQ)](FAQ.md)

## Invitation to Build   
I'm an independent researcher in the middle of a series of papers and a book on applied “edge epistemology.” I have too many time commitments to ship and maintain code. Someone needs to build this before it’s too late.

So here's the design. The first to ship owns the category. If you build it, all I ask is to cite this document and use some of my verbiage. 

Paul Shomo  
Independent Researcher  
[LinkedIn](https://www.linkedin.com/in/paulshomo/) | [@ShomoBits](https://x.com/ShomoBits)
