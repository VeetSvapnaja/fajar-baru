TEX           = lualatex
HTMLTEX       = make4ht
HTMLTEX_FLAGS = 'html, NoFonts'
CUSTOMCSS     = ../tex4ht/enhanced.cfg
CSS_DIR	      = ../tex4ht/css
AUXFILES      = $(wildcard *.aux *.tmp *.toc *.xref *.lg *.idv *.dvi *.4tc *.4ct *.out *.log)
SOURCES       = book.tex
PDFS          = $(SOURCES:.tex=.pdf)
HTML          = $(SOURCES:.tex=.html)
MKDIR_P	      = mkdir -p
OUT_DIR	      = build
OUT_HTML      = $(OUT_DIR)/html
OUT_PDF       = $(OUT_DIR)/pdf
.PHONY: rmaux pdf html clean all directories

all: directories pdf html

pdf: $(SOURCES) $(PDFS)

html: $(SOURCES) $(HTML)

clean: rmaux
	rm -f $(PDFS) $(HTML)

directories: ${OUT_DIR}

${OUT_DIR}:
	${MKDIR_P} ${OUT_DIR}
${OUT_HTML}:
	${MKDIR_P} ${OUT_HTML}
${OUT_PDF}:
	${MKDIR_P} ${OUT_PDF}

rmaux:
	rm -f $(AUXFILES)

pdf: $(SOURCES) $(OUT_PDF)
	$(TEX) -output-directory=$(OUT_PDF) $(SOURCES)

html: $(OUT_HTML)
	$(HTMLTEX) -c $(CUSTOMCSS) $(SOURCES) -d $(OUT_HTML)
	cp -r $(CSS_DIR) $(OUT_HTML)
