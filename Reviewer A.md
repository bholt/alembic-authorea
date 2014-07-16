## Reviewer A

> Partitioning a program using computation migration to avoid communication goes back to at least the early 90s. Hsieh, Wang and Weihl looked at translating programmer annotations of migrateable tasks into continuations that could be moved to data (PPoPP '93, SC '96). Rogers et al (TOPLAS '95) and Carlisle and Rogers (PPoPP '95) looked at dynamically choosing whether to migrate tasks to data or not, again using something that looks like migrating computation -- the programming model even looks roughly like PGAS, with data structures distributed across heaps that individual processes own.

Added a paragraph, *Early DSM systems*, in Section 6.1 to cite these.

> More recently, there has been a lot of work on automatically partitioning programs between devices for computation offloading (Wang and Franz, 2008; Wang and Li, PLDI 2004) or even for security (Chong et al, SOSP '04), which has a similar flavor: certain statements in a program are "anchored" to an execution site.

Added section 6.2 to address this class of computation offloading techniques.

> The approach of dividing programs up between phases that execute at different locations by, essentially, partitioning a dependence graph, also has some similarities to David August's DSWP work.

Section 4.2.2 (second paragraph) now cites DSWP in reference to similar techniques which partition the dependence graph.

> One thing that is not clear is whether individual statements in a program must only be part of one region...
> Are regions intended to be contiguous chunks of code? ...

The first few paragraphs of Section 4.2 attempt to establish how instructions are placed in a single, contiguous region by design, which means they cannot overlap, that instructions are only ever moved to the previous region, and that lifting these restrictions is simply left for future work.

> Instruction hoisting isn't done until code is generated, correct? What if two regions are extended based on incompatible hoisting decisions?

The penultimate paragraph in 4.2.3 now explains this.

> When describing the programming model in Section 3, it's not clear whether you are describing restrictions on the programming model that the programmer must adhere to, or constraints on generated code that the compiler must enforce. Who actually determines the locales of objects?

Added some explanation earlier in section 3.1, and I believe the last paragraph in section 3.1 should answer most of the rest of this.

> Figure 1b is never really explained. It appears to be a standard dependence graph, with one node per statement, but the node labels do not make it clear which statement each node represents.

Now explained in 4.2.2, pararaph 2.
