# tap-sendinblue

`tap-sendinblue` is a Singer tap for Sendinblue.

Built with the [Meltano Tap SDK](https://sdk.meltano.com) for Singer Taps.

## Installation

- [ ] `Developer TODO:` Update the below as needed to correctly describe the install procedure. For instance, if you do not have a PyPi repo, or if you want users to directly install from your git repo, you can modify this step as appropriate.

```bash
pipx install tap-sendinblue
```

## Configuration

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `api_key` | Yes | Sendinblue API key used to authenticate all requests. Found under **SMTP & API > API Keys** in your Sendinblue account. | `xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx` |
| `start_date` | No | Earliest record date to sync. Records with a date before this value are ignored. ISO 8601 format. | `2023-01-01T00:00:00Z` |
| `user_agent` | No | Custom `User-Agent` header value sent with every request. Useful for identifying your integration in API logs. | `tap-sendinblue/1.0 my-company` |

**Note:** `api_key` is the only authentication method supported. You can generate or manage keys in your Sendinblue account under **Settings > SMTP & API > API Keys**. The key is sent as an `api-key` request header.

```json
{
  "api_key": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "start_date": "2023-01-01T00:00:00Z"
}
```

## Usage

You can easily run `tap-sendinblue` by itself or in a pipeline using [Meltano](https://meltano.com/).

### Executing the Tap Directly

```bash
tap-sendinblue --version
tap-sendinblue --help
tap-sendinblue --config CONFIG --discover > ./catalog.json
```

## Developer Resources

- [ ] `Developer TODO:` As a first step, scan the entire project for the text "`TODO:`" and complete any recommended steps, deleting the "TODO" references once completed.

### Initialize your Development Environment

```bash
pipx install poetry
poetry install
```

### Create and Run Tests

Create tests within the `tap_sendinblue/tests` subfolder and
  then run:

```bash
poetry run pytest
```

You can also test the `tap-sendinblue` CLI interface directly using `poetry run`:

```bash
poetry run tap-sendinblue --help
```

### Testing with [Meltano](https://www.meltano.com)

_**Note:** This tap will work in any Singer environment and does not require Meltano.
Examples here are for convenience and to streamline end-to-end orchestration scenarios._

Your project comes with a custom `meltano.yml` project file already created. Open the `meltano.yml` and follow any _"TODO"_ items listed in
the file.

Next, install Meltano (if you haven't already) and any needed plugins:

```bash
# Install meltano
pipx install meltano
# Initialize meltano within this directory
cd tap-sendinblue
meltano install
```

Now you can test and orchestrate using Meltano:

```bash
# Test invocation:
meltano invoke tap-sendinblue --version
# OR run a test `elt` pipeline:
meltano elt tap-sendinblue target-jsonl
```

### SDK Dev Guide

See the [dev guide](https://sdk.meltano.com/en/latest/dev_guide.html) for more instructions on how to use the SDK to 
develop your own taps and targets.
