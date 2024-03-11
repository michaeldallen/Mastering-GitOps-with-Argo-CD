#BOF

.PHONY: test


REG := oci://mw-docker.repositories.mathworks.com

REPO := mallen

APP := httpd

VER := 1.4.7

THIS_MAKEFILE := $(lastword $(MAKEFILE_LIST))

helm.package :
	helm package . --version ${VER}

helm.push : helm.package
	helm push ${APP}-${VER}.tgz ${REG}/${REPO}

all : helm.package helm.push

bumpy :
	@cp ${THIS_MAKEFILE} ${THIS_MAKEFILE}.pre-bumpy ; cat ${THIS_MAKEFILE}.pre-bumpy | awk -F. '/^VER/ { $$(NF - 1) = $$(NF - 1) + 1 ; new_dollar_zero = gensub("([0-9]) ", "\\1.", "g") ; $$0 = new_dollar_zero } { print }' > ${THIS_MAKEFILE}

bumpz :
	@cp ${THIS_MAKEFILE} ${THIS_MAKEFILE}.pre-bumpz ; cat ${THIS_MAKEFILE}.pre-bumpz | awk -F. '/^VER/ { $$(NF - 0) = $$(NF - 0) + 1 ; new_dollar_zero = gensub("([0-9]) ", "\\1.", "g") ; $$0 = new_dollar_zero } { print }' > ${THIS_MAKEFILE}

#EOF
