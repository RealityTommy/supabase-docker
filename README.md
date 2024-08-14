# supabase-docker
## Prerequisites
- [ ] Python 3.12.5
- [ ] Docker
- [ ] Docker Compose
## [Set Up Supabase](https://supabase.com/docs/guides/self-hosting/docker)
1. Clone the supabase repo within the project.
	```
	git clone --depth 1 https://github.com/supabase/supabase
	```
2. Navigate into the docker folder.
	```
	cd supabase/docker
	```
1. Copy the fake env vars.
	```
	cp .env.example .env
	```
4. Pull the latest docker images.
	```
	docker compose pull
	```
5. Start the services (in detached mode).
	```
	docker compose up -d
	```
# [Access Supabase Dashboard](https://supabase.com/docs/guides/self-hosting/docker#accessing-supabase-dashboard)
You can access the Supabase Dashboard through the API gateway on port `8000`. For example: `http://<your-ip>:8000`, or [localhost:8000](http://localhost:8000/) if you are running Docker locally.

You will be prompted for a username and password. By default, the credentials are:
- Username: `supabase`
- Password: `this_password_is_insecure_and_should_be_updated`
## [Dashboard Authentication](https://supabase.com/docs/guides/self-hosting/docker#dashboard-authentication)

The dashboard is protected with Basic Authentication. The default user and password MUST be updated before using Supabase in production. Update the following values in the `.env` file:

- `DASHBOARD_USERNAME`: The default username for the Dashboard
- `DASHBOARD_PASSWORD`: The default password for the Dashboard

You can also add more credentials in `./docker/volumes/api/kong.yml`. For example:

docker/volumes/api/kong.yml

`   1  basicauth_credentials:    2  - consumer: DASHBOARD    3  username: user_one    4  password: password_one    5  - consumer: DASHBOARD    6  username: user_two    7  password: password_two            `

You will need to [restart](https://supabase.com/docs/guides/self-hosting/docker#restarting-all-services) the services for the changes to take effect.