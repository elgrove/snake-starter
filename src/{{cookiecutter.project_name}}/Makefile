lint:
	-poetry run docformatter -r --in-place --black {{cookiecutter.project_name}} core || [ $$? -eq 3 ] # accept error code 3 as success
	poetry run black {{cookiecutter.project_name}} core
	poetry run isort {{cookiecutter.project_name}} core
	poetry run flake8 {{cookiecutter.project_name}} core
	poetry run pylint {{cookiecutter.project_name}} core


test:
	@bash -c 'poetry run pytest ; \
    EXIT_CODE=$$? ; \
    if [ -z "$$EXIT_CODE" ]; then exit 1 ; \
    elif [ $$EXIT_CODE -eq 5 ]; then exit 0 ; \ # accept exit code 5 as success
    else exit $$EXIT_CODE ; \
    fi'
