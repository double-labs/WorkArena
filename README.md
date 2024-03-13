# 🤖💻 WorkArena - How Capable are Web Agents at Solving Common Knowledge Work Tasks?

[[Paper]](https://arxiv.org/abs/2403.07718) ♦ [[Benchmark Contents]](#benchmark-contents) ♦ [[Getting Started]](#getting-started) ♦ [[BrowserGym]](https://github.com/ServiceNow/BrowserGym) ♦ [[Citing This Work]](#citing-this-work)

`WorkArena` is a suite of browser-based tasks tailored to gauge web agents' effectiveness in supporting routine tasks for knowledge workers. 
By harnessing the ubiquitous [ServiceNow](https://www.servicenow.com/what-is-servicenow.html) platform, this benchmark will be instrumental in assessing the widespread state of such automations in modern knowledge work environments.

WorkArena is included in [BrowserGym](https://github.com/ServiceNow/BrowserGym), a conversational gym environment for the evaluation of web agents.


## Benchmark Contents

At the moment, WorkArena includes `23,150` task instances drawn from `29` tasks that cover the main components of the ServiceNow user interface. The following videos show an agent built on `GPT-4-vision` interacting with every such component. As emphasized by our results, this benchmark is not solved and thus, the performance of the agent is not always on point.

### Knowledge Bases

**Goal:** The agent must search for specific information in the company knowledge base.

_The agent interacts with the user via BrowserGym's conversational interface._

https://github.com/ServiceNow/WorkArena/assets/1726818/e2c54e47-a161-4d41-a553-66f9031f075d

### Forms

**Goal:** The agent must fill a complex form with specific values for each field.

https://github.com/ServiceNow/WorkArena/assets/1726818/03a3250f-7ed9-4bbc-837f-7f381a65d351

### Service Catalogs

**Goal:** The agent must order items with specific configurations from the company's service catalog.

https://github.com/ServiceNow/WorkArena/assets/1726818/85f71b9e-6680-4961-940b-d05163f4206a

### Lists

**Goal:** The agent must filter a list according to some specifications.

_In this example, the agent struggles to manipulate the UI and fails to create the filter._

https://github.com/ServiceNow/WorkArena/assets/1726818/d28c62ee-7fde-4a3c-af6d-ea9e2637351d

### Menus

**Goal:** The agent must navigate to a specific application using the main menu.

https://github.com/ServiceNow/WorkArena/assets/1726818/1371862f-0cbb-46f3-9424-a6819afad035

## Getting Started

To setup WorkArena, you will need to get your own ServiceNow instance, install our Python package, and upload some data to your instance. Follow the steps below to achieve this.

### a) Create a ServiceNow Developer Instance

1. Go to https://developer.servicenow.com/ and create an account.
2. Click on `Request an instance` and select the `Vancouver` release (initializing the instance will take a few minutes)
3. Once the instance is ready, you will see a popup showing its URL and credentials. You will also receive a copy by email. Based on this information, set the following environment variables:
    * `SNOW_INSTANCE_URL`: URL of your ServiceNow developer instance
    * `SNOW_INSTANCE_UNAME`: Just use "admin"
    * `SNOW_INSTANCE_PWD`: The password for your instance. Make sure you place the value in quotes "" since it might contain special characters.
4. Log into your instance via a browser using the admin credentials. Close any popup that appears on the main screen (e.g., agreeing to analytics).

**Warning:** Feel free to look around the platform, but please make sure you revert any changes (e.g., changes to list views, pinning some menus, etc.) as these changes will be persistent and affect the benchmarking process.

### b) Install WorkArena and Initialize your Instance

Run the following command to install WorkArena in the [BrowswerGym](https://github.com/servicenow/browsergym) environment:
```
pip install browsergym-workarena
```

Then, run this command in a terminal to upload the benchmark data to your ServiceNow instance:
```
workarena-install
```

### c) Validate Your Installation

The are a lot of moving parts (authentication credentials, benchmark data, etc.) so we highly recommend that you sanity-check your installation using our provided unit tests. Do this by running (might take a few minutes):
```
pytest -v .
```

Your installation is now complete! 🎉


## Citing This Work

```
@misc{workarena2024,
      title={WorkArena: How Capable Are Web Agents at Solving Common Knowledge Work Tasks?}, 
      author={Alexandre Drouin and Maxime Gasse and Massimo Caccia and Issam H. Laradji and Manuel Del Verme and Tom Marty and Léo Boisvert and Megh Thakkar and Quentin Cappart and David Vazquez and Nicolas Chapados and Alexandre Lacoste},
      year={2024},
      eprint={2403.07718},
      archivePrefix={arXiv},
      primaryClass={cs.LG}
}
```