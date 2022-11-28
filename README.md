API_YAMDB
REST API ������ ��� ������� YaMDb � ���� ������� � �������, ������ ��� ������.

��������
������ YaMDb �������� ������ ������������� �� ������������. ������������ ������� �� ���������: ������, ��������, �������. ������ ��������� ����� ���� �������� (��������, ����� �������� ��������� ���������������� ��������� ��� ���������).

��� ��������� ������:
��� ��������� ���� ��������� � �� Linux. ��������� ����������� � ��������� � ����:

git clone https://github.com/themasterid/infra_sp2
cd infra_sp2
cd api_yamdb
������� � ���������� ����������� ���������:

python3 -m venv venv
source /venv/bin/activate (source /venv/Scripts/activate - ��� Windows)
python -m pip install --upgrade pip
������ ����������� �� requirements.txt:

pip install -r requirements.txt
��������� � ����� � ������ docker-compose.yaml:

cd infra
��������� ���������� (infra_db_1, infra_web_1, infra_nginx_1):

docker-compose up -d --build
��������� ��������:

docker-compose exec web python manage.py makemigrations reviews
docker-compose exec web python manage.py migrate
������� �����������������:

docker-compose exec web python manage.py createsuperuser
�������� �������:

docker-compose exec web python manage.py collectstatic --no-input
������� ���� ���� ������ (��� � ������� �����������):

docker-compose exec web python manage.py dumpdata > dumpPostrgeSQL.json
������������� ����������:

docker-compose down -v
������ ���������� .env (�� ������� � ������� �����������) ������������� �� ���� infra/.env
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
