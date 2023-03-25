
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ChatGPT API access via R session

This package is a retooling of <https://github.com/jcrodriguez1989/chatgpt> by jcrodriguez1989. I wanted to use their package for research with chatGPT. However, this API package
forced input prefixes that would prime chatGPT to respond to questions realting to R. While this is great for asking chatGPT to work with R code, I wanted to have API 
access in an R session without any pre-defined priming (for research purposes). I also added up some additional parameters for that the OpenAI API provides in
their documentation.


## Installation

You can install the development version of {chatGPTapi} from
[GitHub](https://github.com/zr159811/chatGPTapi) with:

``` r
# install.packages("remotes")
remotes::install_github("zr159811/chatGPTapi")
```

## Requirements

You must first create a ChatGPT API key.

First you will need to obtain the ChatGPT API key. You can create an
API key by going to [OpenAI API
page](https://beta.openai.com/account/api-keys)

Then you have to assign your API key for usage in R, this can be done
just for the actual session, by doing:

``` r
Sys.setenv(OPENAI_API_KEY = "XX-XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX")
```

Or you can do it persistent (session-wide), by assigning it in your
`.Renviron` file. For it, execute `usethis::edit_r_environ()`, and in
that file write a line at the end your API key as

``` r
OPENAI_API_KEY=XX-XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
```

## Features

There is only one function in this simple package. 

- **askgpt:** Sends a prompt to the chatGPT API and returns a response. 


## Code Examples

#### `askgpt`

``` r
> cat(askgpt("How are you?"))

ChatGPT input:

How are you?
I am an AI language model, so I don't have feelings or emotions. However, I am functioning well and ready to assist you in any way I can. How can I assist you today?
```


## Additional Parameters

### Disable Console Messages

If you want {chatGPTapi} not to show messages in console, please set the
environment variable `OPENAI_VERBOSE=FALSE`.


### ChatGPT Model Tweaks

ChatGPT model parameters can be tweaked by using environment variables.

The following environment variables variables can be set to tweak the
behavior, as documented in
<https://beta.openai.com/docs/api-reference/completions/create> .

- `OPENAI_MODEL`; defaults to `"gpt-3.5-turbo"`
- `OPENAI_MAX_TOKENS`; defaults to `256`
- `OPENAI_TEMPERATURE`; defaults to `1`
- `OPENAI_TOP_P`; defaults to `1`
- `OPENAI_N_COMPLETIONS`; defaults to `1`
- `OPENAI_FREQUENCY_PENALTY`; defaults to `0`
- `OPENAI_PRESENCE_PENALTY`; defaults to `0`
