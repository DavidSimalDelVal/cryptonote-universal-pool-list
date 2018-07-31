# Add or update your pool

Change about pools are managed with pull requests.
That means you have to do the change your-self and then submit a pool request.

## Setup environment

The second step is to setup and start the dev environment.

Install the dependencies:

```bash
npm install
```

From another terminal, start the backend in watching mode:

```bash
npm run w:back:<currency symbol>
```

Presently, the currency symbols are:

- btn
- gdm

Start the frontend in watching mode:

```bash
npm run w:front
```

Once the page is opened go to https://localhost:9000/<currency name>.html

The currency names are:

- btn
- gdm

## Apply your change

### How-to add a new pool?

New pool are defined in a new JSON file.
The path is `src/config/<currency>/<domain name>.json`.

The structure is:

```json
{
    "name": "<domain name>",
    "front": "<URL to front end>",
    "back": "<URL to backend end>",
    "location": "<localization>",
    "impl": "<nodejs-pool or cryptonote-universal-pool>",
    "disabled": false
}
```

For instance, about a pool backed by nodejs-pool:

```json
{
    "name": "www.geldumpool.com",
    "front": "http://www.geldumpool.com",
    "back": "http://www.geldumpool.com:8118",
    "location": "US",
    "impl": "nodejs-pool",
    "disabled": false
}
```

For instance, about a pool backed by cryptonote-universal-pool:

```json
{
    "name": "www.geldumpool.com",
    "front": "http://www.geldumpool.com",
    "back": "http://www.geldumpool.com:8118",
    "location": "US",
    "impl": "cryptonote-universal-pool",
    "disabled": false
}
```

Once the change done, the backend will detect the change and reload the pool list.
From the front-end you just need to refresh the pool list.

### How-to update an existing pool?

To update an existing pool, you just need to edit the right file, i.e. `src/config/<currency>/<domain name>.json`.
Once the change done, the backend will detect the change and reload the pool list.
From the front-end you just need to refresh the pool list.

You can use the boolean `disabled` to virtually remove the pool from the list.

## Submit the pool request

Once change done, you can push the change to the forked repository.
Then from the github interface you should be able to submit a pool request to the official repository.
Once submitted the pool will be review and merged.
