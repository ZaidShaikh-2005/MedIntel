# Local configuration

The private source was unavailable when this documentation package was prepared. Use the settings and dependency definitions in your checkout as the authority for version numbers and configuration names.

## Python and dependencies

- Choose a Python version compatible with the project’s Django version.
- Create a fresh virtual environment.
- Install dependencies from the project’s requirements file or package definition.
- Use the existing dependency versions before considering upgrades.

If a requirements file is present at the repository root:

```bash
python -m pip install -r requirements.txt
```

## Services

| Component | Configuration to inspect |
| :--- | :--- |
| Django | Settings module referenced by `manage.py`, application secret, local development options, and allowed hosts |
| Database | Database engine, name, connection details, and any required driver |
| MQTT | Broker address, port, authentication, topic names, sensor payload schema, and listener startup |
| ESP32 | Network configuration, broker connection, supported sensors, and payload mapping |
| ML inference | Model artifact paths and the preprocessing expected by the trained model |
| Ollama | Installed runtime, application endpoint, configured model tag, and available machine resources |

Use the configuration mechanism already supported by the application. This package does not add an environment-variable loader or invent setting names.

## Django startup

Once dependencies, database access, and configuration are ready, run these from the directory containing `manage.py`:

```bash
python manage.py check
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

The MQTT ingestion service and AI runtime may need separate startup commands. Consult their entry points in the source.

## References

- [Django development server](https://docs.djangoproject.com/en/5.2/intro/tutorial01/#the-development-server)
- [Django database setup](https://docs.djangoproject.com/en/5.2/intro/tutorial02/#database-setup)
- [Django admin user](https://docs.djangoproject.com/en/5.2/intro/tutorial02/#creating-an-admin-user)
- [Ollama quickstart](https://docs.ollama.com/quickstart)

Select Django documentation matching the version actually installed in your project.
