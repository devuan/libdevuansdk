all: clean html man

html:
	@echo generating html...
	@./nanodoc html

man:
	@echo generating manpages...
	@./nanodoc man

clean:
	@echo cleaning...
	@rm -rf html man nav.html
	@sed -i -e 's:index.html">.*:html">NAME</a>:' static/head.html
	@sed -i -e 's:Subtitle">.*:Subtitle">DESC</span>:' static/head.html
	@sed -i -e 's:libdevuansdk-.*:libdevuansdk-VERSION</a>:' static/foot.html

.PHONY: all html man clean
