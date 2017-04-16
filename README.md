# scripts
Scripts to process the different data files

**TrieConvert.py**:  used by convert_pp.py and convert_pp4.py and convert_pp_pass2.py

**convert_pp.py**: converts from betacode to UTF-8, post-proc sigmas. Creates BRAT files.

```bash
Example:
python3 convert_pp.py -f plat.laws_gk.xml
```

**convert_pp4.py**: converts from betacode to UTF-8, post-proc sigmas. Creates BRAT files. Does speaker-IDs ublike convert_pp.py

```bash
Example:
python3 convert_pp4.py -f plat.laws_gk.xml
```

**convert_pp_pass2.py**: Takes output from convert_pp4.py and makes the final BRAT version. Splits also in chapters/books.

```bash
Example:
python convert_pp4.py -f thuc.hist_gk.xml
python convert_pp_pass2.py -f thuc.hist_gk.brat -b -c -r
  (tar and upload all *txt/*ann files to /scratch2/www/brat/data/ThucydidesP
  fix permissions on all files.
  copy annotation.conf, tools.conf, visual.conf)
```

**bratstats.py**: Counts statistics on brat .txt and .ann files

```bash
Example: (specify the *txt files (wildcards are expanded))
python3 bratstats.py -f "thuc.hist_gk.brat.book6*.txt"
```

**compare_wlt.py**: Compares two wlt files, or one stats and one wlt file.

**conllXtostandoff.py**:  Script to convert a CoNLL X (2006) tabbed dependency tree format file into BioNLP ST-flavored standoff and a reconstruction of the original text.

**convert_perseus_csv.py**: converts /Users/pberck/Downloads/hib_parses_uc.csv to word-lemma-tag. Used to make perseus-wlt.txt

```bash
Example:
python3 convert_perseus_csv.py > hib_parses_uc.csv.wlp
python3 rewrite_perseus.py -f hib_parses_uc.csv.wlp > hib_parses_uc.csv.wlp.rwrt
(cp hib_parses_uc.csv.wlp.rwrt ~/SurfdriveRadboud/Shared/PerspectiveProject/GreekPerspectives/Software/Lemmatizer/Scripts/perseus-wlt.txt)
```

**convert_tags.py**: Converts the part-of-speech=".." and  morphology=".." tag to an all inclusive postag. 

```bash
Input filename hdt.xml en output filename hdt.postag.xml zijn hard-coded. 
hdt.xml moet in dezelfde directory liggen als convert_tags.py. 
Leest de mapping uit tagsmap.txt in dezelfde directory
```
 
**merge_proiel_perseus.py**:  Merget de twee output files van rewrite_proiel en rewrite_perseus.

```bash
Example:
python3 merge_proiel_perseus.py -f greek_Haudag.pcases.lemma.lex.rewrite -F perseus-wlt.txt > proiel_v2_perseus_merged.txt
```

**mybeta2unicode.py**: adapt to TEI xml format of Thucydides, (c) James Tauber

**rewrite_perseus.py**: Eerste conversie SQL dump - de output heeft een tweede conversie slag nodig om de complexere P tags erin te zetten.

```bash
Example:
python3 rewrite_perseus.py -f hib_sqldump_word_lemma_tag.utf8 > hib_sql.out.txt

(venv) durian:lemmatiser pberck
python3 rewrite_perseus.py -f 04_perseus/d638f82gs4.txt.utf8b > 04_perseus/d638f82gs4.txt.utf8b.rwrt
```

**rewrite_proiel_v3.py**: Rewrites tags in greek_Haudag.pcases.lemma.lex, uses info from perseus-wlt.lex.

```bash
Example:
python3 rewrite_proiel_v3.py > greek_Haudag.pcases.lemma.lex.rewrite_new
```
