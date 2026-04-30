# Co-Wiki and REM Agent — Frequently Asked Questions (FAQ)

## Where's the install link, I want to extend my brain daily with the Co-Wiki?

The Co-Wiki and REM Agent isn't a finished product — it's an open design and an open architecture. It's waiting for developers to build.

The formally verified engine is live at cowiki.tech. The remaining open invitation is the DokuWiki backend integration and the full human-agent co-authorship UI layer — the piece that completes the Legible Memory Layer as designed.

The architecture is documented, copyright registered CC BY 4.0, and published as an open invitation to build.

## Why do I have to build your design? Why don't you whip out Claude Code and build it for us?

Because I'm a hyper-competitive and obsessive perfectionist, and if I take on building and maintaining this in 2026, it will rule my life. I'm 100% booked with high priority projects right now.

Yet I released an open source design because I believe a Co-Wiki will someday become the dominant UX design in text-based LLM-human interactions. Further, that the Legible Memory Layer and Co-Wiki graph search via flat wiki files represent a novel architecture. I actually want to use this thing once it is built, and I wanted credit for the idea. I believe these ideas could be big in the future.

[@copyleftdev](https://github.com/copyleftdev) took time from his 383+ Git repos and day job to build a formal proof of the spreading activation graph search and an architectural implementation.

If you have the skills and want to build and/or maintain a high-profile open source project, please take hold of the Co-Wiki and REM Agent.

## Has anyone built a working implementation of the Co-Wiki architecture?

Yes. Within 48 hours of the Co-Wiki manifesto being published in April 2026, Don Johnson ([@copyleftdev](https://github.com/copyleftdev)) built a formally verified Rust implementation: [cowiki-rs](https://github.com/copyleftdev/cowiki-rs).

The implementation includes:

- 7 Rust crates with 133 tests and 0 unsafe code
- Formally verified spreading activation primitives (Banach fixed-point theorem)
- A chaos testing gauntlet running 22,500 adversarial operations against every proven invariant
- A three-panel demo UI with live performance counters, stress testing, and REM Agent controls
- A Dockerized one-command install: `make demo`
- A live demo at [cowiki.tech](https://cowiki.tech)

**Performance results:**
- Query latency: 27μs p50, 36,400 queries per second
- Query "memory sleep consolidation": spreading activation finds 7 pages in 68 microseconds. Vector search finds one.

**From the formal proof suite (PROOF.md):** Nine architectural claims were tested. Seven were proven including linear spreading activation as a contraction mapping (Banach fixed-point theorem), graph retrieval beating vector retrieval on associative queries, and REM decay/prune/dream operators maintaining graph health. Two claims were disproven and corrected — the corrections strengthened the model.

The implementation uses a custom wiki filesystem backend rather than DokuWiki, and the full human-agent co-authorship UI layer remains the open invitation to the developer community.

## I don't want to browse a wiki, I just want to chat with an LLM and search my Vector DB.

If you're okay with creating and managing chat threads, the Co-Wiki is not for you.

If you never want to edit the output of old AI interactions directly, the Co-Wiki is not for you.

The Co-Wiki is for you if you look at the standard wiki (e.g. DokuWiki) user experience and workflows and think, "I wish I could store all the past work I've done in LLM chats in wiki pages like this, and manage them through a hybrid of DokuWiki + LLM Chat interface."

## What is the key retrieval difference between the Co-Wiki and RAG?

Standard RAG (Retrieval-Augmented Generation) architectures embed documents and retrieve by vector similarity. You ask a question, the system finds the chunks most semantically similar to your query, and returns them. It's designed for flat corpora — large collections of documents with no explicit relationship structure. That's the right tool for querying a document repository.

The Co-Wiki is designed for a different problem: your extended cognition. The knowledge you return to, refine, and connect over months. A flat index can't capture that topology. A knowledge graph built by you and a REM Agent can.

The retrieval difference is structural. RAG queries an index. The Co-Wiki traverses a knowledge graph built by a human author and a REM Agent working together over time. Spreading activation propagates through that backlink structure and surfaces the associative neighborhood — not just the closest semantic match.

Don Johnson's formally verified prototype demonstrates this directly. Query "memory sleep consolidation": vector search returns 1 page, spreading activation returns 7 pages in 68 microseconds. The difference isn't the algorithm — it's the knowledge structure the Co-Wiki builds over time that makes richer retrieval possible.

RAG doesn't compound. The Co-Wiki does.

Independent academic research is converging on the same conclusion. The SYNAPSE paper (Pavlović et al., 2026) argues that standard RAG suffers from "Contextual Isolation" — a failure mode stemming from what it calls the "Search Assumption": that the relevance of a past memory is strictly determined by its semantic proximity to the current query. SYNAPSE proposes spreading activation over a knowledge graph as the solution, demonstrating that graph-based retrieval surfaces causally and associatively related memories that share no lexical or embedding overlap with the query. The Co-Wiki architecture was published independently and reached the same conclusion from first principles.

## What is the Legible Memory Layer?

The Legible Memory Layer is the Co-Wiki's core architectural principle — warm storage that is readable by both humans and agents, browsable, versionable, and structured by the cognitive grain of the person using it.

It is not a database. It is not a vector index. It is a living knowledge workspace.

The full wiki experience — splitting a page when a concept outgrows its container, merging two pages when you realize they're the same idea, diffing to see how your thinking evolved — is not just UX. These are ontological operations. When you and the agent split and link pages together, you are pre-chunking and connecting the knowledge in a form that spreading activation can traverse at query time. The chunking emerges from how humans and agents naturally think and write together, not from an algorithm carving up a document after the fact.

This is what makes the Co-Wiki an extension of cognition rather than just a memory store.

## When does the Co-Wiki search my cold storage?

The Co-Wiki is a warm storage system only. It builds, maintains, and searches all top-of-mind and adjacent information in this warm storage using a knowledge graph.

If something cannot be found in warm storage, your AI system still needs its own cold storage search.

## Why a new architecture? Is the Co-Wiki really flatter with fewer components than Andrej Karpathy's LLM Knowledge Base? Isn't DokuWiki a complex architecture layer?

Karpathy's [LLM Knowledge Base](https://x.com/karpathy/status/2039805659525644595) is composed of the Obsidian front end and visualizations, command line tools, the Obsidian Vault wiki, and would require Git for versioning.

The [Co-Wiki](co-wiki-rem-agent.md) is a wiki like DokuWiki and an LLM enabled with mutual filesystem access. For reading and searching, no infrastructure or API integration is even needed.

Writing and maintenance operations by the REM Agent, that automatically maintains the wiki, would require API integration for atomic operations.

## How does the UI and workflow compare to Karpathy's?

Karpathy's is primarily based on LLM chat and uses Obsidian for visualizations. His wiki is mainly a one-way output — not something you'd edit directly. It also doesn't have wiki-specific workflows for pruning, diffing, or approving agent changes to pages, or examining what's automatically versioned.

In Karpathy's system, the user moves between multiple UIs: wiki, Obsidian visualizations, the command line, and Git for versioning. As Karpathy [said](https://x.com/karpathy/status/2039805659525644595), "I think there is room here for an incredible new product instead of a hacky collection of scripts." A flat file based wiki like DokuWiki is the codebase to begin this from.

In the Co-Wiki, LLM chat would still be a major workflow on top of the wiki pages. Yet the Co-Wiki also showcases the classic wiki workflows for reading, editing, organizing "top of mind" content, and approving and versioning — all in one UI.

At LLM Chat Session Close, or Wiki Page Edit Close, one could innovate on both the standard LLM chat UIs, or the DokuWiki page edit UIs to have the best of both worlds: LLM chat + wiki.

The Co-Wiki design is meant to automatically handle "Wiki Gardening" through the REM Agent's DokuWiki API integration. Karpathy's system includes linting scripts that perform similar functions when triggered manually.

## What is the key retrieval difference between the Co-Wiki and Karpathy's LLM Knowledge Base?

This is the most important architectural distinction between the two designs.

Karpathy's system and the Co-Wiki share the same flat file foundation — both use markdown files with explicit backlink relationships that form a knowledge graph. The architectural divergence is at the retrieval layer.

Karpathy queries embeddings against his Obsidian flat files using vector similarity search. The backlink graph his system builds is not traversed at query time. The graph exists. It just isn't being used for retrieval.

The Co-Wiki traverses that graph using spreading activation — a retrieval mechanism first described by Collins and Loftus in 1975 as a model of how human associative memory works. Rather than returning the single closest semantic match, spreading activation propagates through the backlink structure and surfaces the associative neighborhood.

Don Johnson's formally verified Rust implementation proves the difference empirically. Query "memory sleep consolidation" against the same knowledge graph: vector search returns 1 page, spreading activation returns 7 pages in 68 microseconds.

Karpathy is doing the right maintenance work — his manual linting scripts tend the graph over time. He just isn't getting the retrieval benefit from the graph he's building.

## How does the Co-Wiki compare to Nate B. Jones' Open Brain?

While Karpathy's is a semi-wiki solution, Nate's isn't a wiki at all.

OB1 is a Postgres database with vector search, an MCP server for standardized AI tool access, and a chat interface. It solves a real and distinct problem: every AI tool you use has no memory of the last one. OB1 gives all your AI tools a shared persistent memory layer accessible across Claude, ChatGPT, Cursor, and any other MCP-compatible tool.

Nate's argument is that every time an LLM creates a wiki page it makes editorial or synthesis choices that could drop important context. He argues the hard thinking should happen at query time using structured data, not at write time building a wiki. His critique of the wiki centers on the Wiki Gardening problem — maintenance, staleness, and drift.

This is a compelling argument for analytics and historical structured querying. But it describes a different problem than the Co-Wiki is solving.

The Co-Wiki's answer to the Wiki Gardening problem is the REM Agent — autonomous background maintenance that discovers new backlinks, decays stale knowledge, and prunes the graph without user intervention. The classic wiki weakness Jones identifies is precisely the opportunity the REM Agent addresses, drawing on the biomimicry of human sleep consolidation.

Three designs, three different bets:

**OB1** — hard thinking at query time, structured database, optimized for cross-tool persistence and analytics. Ships today at $0.10/month.

**Karpathy** — hard thinking at write time, LLM-authored wiki, optimized for research knowledge organization. Manual maintenance.

**Co-Wiki** — hard thinking at write time, human-agent co-authored wiki, optimized for extended cognition and associative retrieval. Autonomous REM Agent maintenance. Graph compounds in quality over time.

These are not necessarily competing. OB1 as your cross-tool memory persistence layer, the Co-Wiki as your extended cognition workspace — the architecture supports both.

For a deeper contrast of the OB1 and Karpathy approaches, Nate B. Jones published a [video](https://www.youtube.com/watch?v=dxq7WtWxi44) directly comparing them. Watch particularly from the 27-minute mark.

## How does the Co-Wiki compare to the classic 5 Layers of Agent Memory?

Some have asked about this [popular](https://champaignmagazine.com/2025/10/14/long-term-memory-for-llms-2023-2025/) layering approach. The Co-Wiki consolidates layers 2–4 into one Legible Warm Storage layer:

### Hot Storage

**1. Working Memory (Immediate Context)**

Co-Wiki is exactly like all standard AI systems: LLM + working memory enables AI interactions.

### Warm Storage

**2. Session Memory (Conversation Continuity)**

**3. Condensed Memory (Lossy Summarization)**

**4. Durable Memory (Persistent Storage)**

Session, Condensed and Durable memory layers are stored inside the Co-Wiki — the legible warm storage layer in this flat architecture. At some point data may be aged out of warm storage by the REM Agent and moved into cold storage.

### Cold Storage

**5. Retrieval Memory (Dynamic Loading)**

Cold storage is in the vector DB.

### Why the Warm Storage and Retrieval Obsession

AI doesn't write down what it learns and the synthesized thought that evolves while working with a user. An LLM doesn't have a clear way to selectively load the data, arguments, and conclusions from previous days of collaboration. It routinely restarts with incomplete context, burning tokens every session to reconstruct what it already worked through.

Nothing has been pre-built without an evolving warm storage layer. The Co-Wiki addresses this directly.

## Do I have to add wiki pages or metadata, such as backlink meta files, to my vector DB for the Co-Wiki to work?

No, the Co-Wiki doesn't need cold storage (vector DB) to find things in its own warm storage.

An LLM is able to ascertain what's in legible memory from DokuWiki's flat file backend, with only minimal prompting. A lightweight preprocessing step converts DokuWiki's metadata files into human-readable companion files, after which the full knowledge graph is accessible without any API or infrastructure. Prompts only.

## Can the Co-Wiki compile data from my cold storage to hold in warm storage?

Admittedly, this was not part of the original design doc. I envisioned warm storage as being built anew as you chatted and searched with your LLM.

Cold storage search results can be harvested into Co-Wiki warm storage pages at session close, using the same session harvest workflow described in the main document.

---

*Paul Shomo — Independent Researcher*
[LinkedIn](https://www.linkedin.com/in/paulshomo/) | [@ShomoBits](https://x.com/ShomoBits)
© 2026 Paul Shomo. All rights reserved.
