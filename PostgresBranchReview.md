[wiki:PostgreSqlProject Main Project Page]

=== Discussion Topics  ===

The topics listed here are being discussed on the mailing list.  They are summarized here for tracking purposes only.

1. Don't want to see a big merge commit land in master.
    * Redo work and group commits into feature-based autonomous commits that can be cherry picked into master, reviewed, tested?
    * Merge and rely on ''diffing'' installed schema(s) to verify semantic equivalence?

2. When ''common'' table (.sql) files created from rhnsat/tables/ - reformatting makes diffs useless.
    * Redo work preserving as much as possible?
    * Merge and rely on ''diffing'' installed schema(s) to verify semantic equivalence?

3. Consolidating the ''upgrade'' .sql scripts into a single (ordered) .sql file for upgrades causes downstream packaging problems.

4. ''Make'' vs. ''Blend'', why not continue with current {{{Makefile.schema}}}?

5. Why use ''chameleon''?
    * Why not templating?
    * Why not search-and-replace approach using something cobbled up with available technology such as ''sed'', ''awk'', etc ...?