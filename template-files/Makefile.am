SUBDIRS = src tests resources

.ctags-file-list:
	echo $(SKELETON_PROJECT_CFLAGS) | awk -F ' -I' \
		'{ for (i=2; i < NF; i++) print $$i > ".ctags-file-list"}'

tags: .ctags-file-list
	$(CTAGS) $(AM_CTAGSFLAGS)

