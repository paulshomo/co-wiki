# Co-Wiki and REM Agent — Frequently Asked Questions (FAQ)

## 1. Why a new architecture? Is the Co-Wiki really flatter with fewer components than Andrej Karpathy's LLM Knowledge Base? Isn't DokuWiki a complex architecture layer?

Karpathy's [LLM Knowledge Base](https://x.com/karpathy/status/2039805659525644595) is composed of the Obsidian front end and visualizations, command line tools, the Obsidian Vault wiki, and would require Git for versioning.

The [Co-Wiki](co-wiki-rem-agent.md) is a wiki like DokuWiki and an LLM enabled with mutual filesystem access. For reading and searching no infrastructure or API integration is even needed.

Writing and maintenance operations by the REM Agent, that automatically maintains the wiki, would require API integration for atomic operations.

## 2. How does the UI and workflows compare to Karpathy's?

Karpathy's is primarily based on LLM chat and uses Obsidian for visualizations. His wiki is mainly a one way output. Karpathy's wiki is not something you'd edit directly. It also doesn't have wiki-specific workflows for pruning, diffing, or approving agent changes to pages, or examining what's automatically versioned.

In Karpathy's system, the user moves between multiple UIs: wiki, Obsidian visualizations, the command line, and you'd need Git for versioning. As Karpathy [said](https://x.com/karpathy/status/2039805659525644595), "I think there is room here for an incredible new product instead of a hacky collection of scripts." I think a flat file based wiki, like DokuWiki, is the codebase to begin this from.

In the Co-Wiki, LLM chat would still be a major workflow on top of the wiki pages. Yet the Co-Wiki also showcases the classic wiki workflows for reading, editing, organizing "top of mind" content, and approving and versioning. All in one UI.

At LLM Chat Session Close, or Wiki Page Edit Close, one could innovate on both the standard LLM chat UIs, or the DokuWiki page edit UIs to have the best of both worlds: LLM chat + wiki.

The Co-Wiki design is meant to automatically handle "Wiki Gardening" through the REM Agent's DokuWiki API integration. Karpathy's system includes linting scripts that perform similar functions when triggered manually.

## 3. I don't want to browse a wiki, I just want to chat with an LLM and search my Vector DB.

If you're okay with creating and managing chat threads, the Co-Wiki is not for you.

If you never want to edit the output of old AI interactions directly, the Co-Wiki is not for you.

The Co-Wiki is for you if you look at the standard wiki (e.g. DokuWiki) user experience and workflows and think, "I wish I could store all the past work I've done in LLM chats in wiki pages like this, and manage them through a hybrid of DokuWiki + LLM Chat interface."

## 4. When does the Co-Wiki search my cold storage?

Co-Wiki is a warm storage system only. It builds, maintains, and searches all top-of-mind and adjacent information in this warm storage using a knowledge graph.

If something cannot be found in warm storage, your AI system still needs its own cold storage search.

## 5. Do I have to add wiki pages or metadata, such as backlink meta files, to my vector DB for the Co-Wiki to work?

No, the Co-Wiki doesn't need cold storage (vector DB) to find things in its own warm storage.

An LLM is able to ascertain what's in legible memory from DokuWiki's flat file backend, with only minimal prompting. A lightweight preprocessing step converts DokuWiki's metadata files into human-readable companion files, after which the full knowledge graph is accessible without any API or infrastructure. Prompts only.

## 6. Can the Co-Wiki compile data from my cold storage to hold in warm storage?

Admittedly, this was not part of the original design doc. I envisioned warm storage as being built anew as you chatted and searched with your LLM.

Cold storage search results can be harvested into Co-Wiki warm storage pages at session close, using the same session harvest workflow described in the main document.

## 7. How does the Co-Wiki compare to the 5 Layers of Agent Memory?

Some have asked about this [popular](https://champaignmagazine.com/2025/10/14/long-term-memory-for-llms-2023-2025/) layering approach. The Co-Wiki mainly consolidated layers 2–4 into one Legible Warm Storage layer:

### Hot Storage

**1. Working Memory (Immediate Context)**

Co-Wiki is exactly like all standard AI systems: LLM + working memory enables AI interactions.

In both the Co-Wiki and Karpathy's LLM Knowledge Base, a knowledge graph is loaded into Working Memory. It was read from Obsidian or DokuWiki's backend flat files.

### Warm Storage

**2. Session Memory (Conversation Continuity)**

**3. Condensed Memory (Lossy Summarization)**

**4. Durable Memory (Persistent Storage)**

Session, Condensed and Durable memory layers are stored inside the Co-Wiki, which is the legible warm storage layer in this flat architecture.

That said, at some point data may be aged out of warm storage by the REM Agent and moved into cold storage (vector DB).

### Cold Storage

**5. Retrieval Memory (Dynamic Loading)**

Cold storage is in the vector DB.

---

*Paul Shomo — Independent Researcher*
[LinkedIn](https://www.linkedin.com/in/paulshomo/) | [@ShomoBits](https://x.com/ShomoBits)
© 2026 Paul Shomo. All rights reserved.
