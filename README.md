# Closed AI

⚠️ **This project is in early development is a work in progress.** ⚠️

`closedai` is a drop-in replacement for `openai`, but only with open models.

## Usage

### Server

In your terminal, run:

```
closedai
```

You can see the available configuration flags with `closedai --help`.

### Client

If using localhost, you can `from closedai import openai`. If running remotely, for now you can just `import openai` and override `openai.api_base` with your endpoint and openai.api_key with a dummy value.

Then, use it as you normally would...

#### Completions

```python
from closedai import openai

completion = openai.Completion.create(model='asdf', prompt='hi there, my name is', stream=False)
print(completion)
```

#### Completions streaming

```python
from closedai import openai

completion = openai.Completion.create(model='asdf', prompt='hi there, my name is', stream=True)
for new_text in completion:
    print(new_text)
```

#### Chat Completions

```python
from closedai import openai

completion = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Who won the world series in 2020?"},
        {"role": "assistant", "content": "The Los Angeles Dodgers won the World Series in 2020."},
        {"role": "user", "content": "Where was it played?"},
    ],
    stream=False,
)
print(completion)
```

#### Chat Completions streaming

```python
from closedai import openai

completion = openai.ChatCompletion.create(
    model="gpt-3.5-turbo",
    messages=[
        {"role": "system", "content": "You are a helpful assistant."},
        {"role": "user", "content": "Who won the world series in 2020?"},
        {"role": "assistant", "content": "The Los Angeles Dodgers won the World Series in 2020."},
        {"role": "user", "content": "Where was it played?"},
    ],
    stream=True,
)

for x in completion:
    print(x)
```
