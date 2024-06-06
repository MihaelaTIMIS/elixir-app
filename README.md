# Doox Application

To start your Phoenix server:

- Install dependencies with `mix deps.get`
- Create and migrate your database with `mix ecto.setup`
- Install Node.js dependencies with `cd assets && npm install`
- Start Phoenix endpoint with `mix phx.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

Ready to run in production? Please [check our deployment guides](https://hexdocs.pm/phoenix/deployment.html).

## Learn more

- Official website: https://www.phoenixframework.org/
- Guides: https://hexdocs.pm/phoenix/overview.html
- Docs: https://hexdocs.pm/phoenix
- Forum: https://elixirforum.com/c/phoenix-forum
- Source: https://github.com/phoenixframework/phoenix
- Alchemist Camp: https://alchemist.camp
- Elixir and Phoenix Bootcamp: https://www.udemy.com
- LearnPhoenix : https://www.learnphoenix.tv
- Elixir School https://elixirschool.com/en/
- Elixir Forum https://elixirforum.com/
- Introduction to Phoenix LiveView LiveComponents http://blog.pthompson.org/liveview-livecomponents-introduction
- Periodic jobs in Elixir with Periodic https://www.theerlangelist.com//article/periodic
- Elixir cheatsheet https://devhints.io/elixir

## How to upgrade Elixir on MacOSX

```
brew update
brew upgrade elixir
```

## Tips

**More Mix**

```
mix help
```

**Test Server in Terminal Elixir**

```
iex  -S mix phx.server
```

**Dependencies**

```
mix deps.update --all
```

**(Mix.Error) Can't continue due to errors on dependencies**

Solution :

1. Set elixirLS.fetchDeps to false.
2. Close VSCode just to be safe.
3. rm -r deps \_build .elixir_ls && mix deps.get.
4. Start VSCode.

# Production

https://phxroad.com/devops/deploy-elixir-phoenix-ubuntu-vps

```
export DATABASE_URL=ecto://USERNAME:PASSWORD@localhost/DATABASE
```

```
mix phx.gen.secret
export SECRET_KEY_BASE=SECRET
```

## Initial setup

```
mix deps.get --only prod
MIX_ENV=prod mix compile
```

## Install / update JavaScript dependencies

```
npm install --prefix ./assets
```

## Compile assets

```
npm run deploy --prefix ./assets
mix phx.digest
```

## Release

```
PORT=4005 MIX_ENV=prod mix release
# Release doox_app-0.1.0 already exists. Overwrite? [Yn]
```

Release created at \_build/prod/rel/doox_app!

### To start your system

`_build/prod/rel/doox_app/bin/doox_app start`

## Once the release is running:

### To connect to it remotely

`_build/prod/rel/doox_app/bin/doox_app remote`

### To stop it gracefully (you may also send SIGINT/SIGTERM)

`_build/prod/rel/doox_app/bin/doox_app stop`

### To list all commands:

`_build/prod/rel/doox_app/bin/doox_app`

# Install PDF Generator

https://hexdocs.pm/pdf_generator/PdfGenerator.html#content

System requirements:
wkhtmltopdf or chrome-headless
pdftk (optional, for encrypted PDFs)

1. (Option for encrypted) Installing PDFtk Server edittion on your Mac
   [Visit](https://gist.github.com/jvenator/9672772a631c117da151)
2. Installing wkhtmltopdf [Visit](https://wkhtmltopdf.org/)
3. add in the file mix.ex : {:pdf_generator, ">=0.6.2", compile: "make chrome" }
   and
   def application do
   [
   extra_applications: [......... :pdf_generator]
   ]
   end
4. add in the file config/config.exs :
   #if you prefer chrome-headless
   config :pdf_generator,
   use_chrome: true,
   prefer_system_executable: true,
   raise_on_missing_wkhtmltopdf_binary: false

```

```
# elixir-app
# elixir-app
# elixir-app
