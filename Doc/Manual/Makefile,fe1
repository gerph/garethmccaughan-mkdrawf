# Makefile for mkdrawf manual.

.SUFFIXES: .draw .src

.src.draw:; mkdrawf $< $@

foo: text ddf
all: text ddf examples

text0: source makemanual; <perl$dir>.perl makemanual -text source > text0
ddf0:  source makemanual; <perl$dir>.perl makemanual -ddf source > ddf0
Text:  text0  fixtext;    <perl$dir>.perl fixtext text0 > Text
ddf ddf-co ddf-ix: ddf0 fixddf
                          <perl$dir>.perl fixddf ddf0 ddf-co ddf ddf-ix

examples: examples.draw.arc examples.draw.koch examples.draw.koch1\
          examples.draw.liss examples.draw.spiral examples.draw.t-area
  stamp examples

examples.src.arc examples.src.koch examples.src.koch1 \
examples.src.liss examples.src.spiral examples.src.t-area: text;

prepare:
  remove Imp
  rename Impression Imp
  copy Impr0 Impression ~C~V

clean:
  remove ddf0
  remove text0
  remove ddf
  remove ddf-co
  remove ddf-ix
  remove Imp

# To make the Impression manual from the three DDF files: drag them
# into the three chapters in a copy of Impr0. But make sure to drag
# "ddf" first, because otherwise some styles will get null definitions
# that then won't be overridden.
