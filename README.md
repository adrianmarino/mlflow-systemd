# MLflow setup

Install mlflow as systemd daemon under linux. This run with your regular linux user.

# Requirements

* miniconda
* mariadb/mysql

# Setup database

```bash
$ mysql -u root -e "CREATE DATABASE IF NOT EXISTS mlflow"
```

# Setup mlflow

**Step 1**: Clone repo. 

```bash
$ cd ~
$ git clone https://github.com/adrianmarino/mlflow-systemd.git
$ mv mlflow-systemd mlflow
$ cd mlflow
```

**Step 2**: Create conda environment required to run mlflow.

```bash
$ conda env update -f environment.yml
```

**Step 3**: Copy service file user level systemd config path:

```bash
$ cp mlflow.service ~/.config/systemd/user/
```

**Step 4**: Refresh systemd daemon with updated config.

```bash
$ systemctl --user daemon-reload
```

**Step 5**: Start service on boot.

```bash
$ systemctl --user enable mlflow
```

**Step 6**: Start mlflow as systemd daemon.

```bash
$ systemctl --user start mlflow
```
