# survival-analysis-public-information-requests
Survival analysis of response times to public information requests using Kaplan–Meier estimation and log-normal regression.


# Survival Analysis of Public Information Request Response Times

## Overview

This repository presents a statistical analysis of response times to public information requests in Brazil, using survival analysis techniques. The study investigates how different communication channels are associated with the time until a governmental entity provides a response.

The project is based on data from the Fala.BR platform and applies time-to-event modeling to evaluate response dynamics, censoring, and differences between request channels.

## Dataset

The dataset contains 147,201 public information requests collected from the Fala.BR platform, covering the period from the second semester of 2020 to the first semester of 2021.

The main variables are:

- `CNS`: request channel
- `TMP`: response time in days
- `TPO`: type of response

Requests still in progress at the time of data collection were treated as censored observations.

## Statistical Methodology

The response variable is the time until the occurrence of the event of interest, defined as the time between the request submission date and the response date.

Let $T$ be the response time. The survival function is defined as:

$$
S(t) = P(T > t)
$$

The Kaplan–Meier estimator was used to estimate survival curves by request channel:

$$
\hat{S}(t) = \prod_{t_i \leq t} \left(1 - \frac{d_i}{n_i}\right)
$$

where:

- $d_i$ is the number of events at time $t_i$
- $n_i$ is the number of requests at risk immediately before $t_i$

In addition to the nonparametric analysis, a log-normal survival regression model was fitted to evaluate the effect of request channels on response time.

The log-normal model assumes:

$$
T_i \sim LogNormal(\mu_i, \sigma)
$$

with:

$$
\mu_i = X_i\beta
$$

The median response time is given by:

$$
Med(T_i) = e^{\mu_i}
$$

This allows interpretation of the model parameters in terms of relative changes in median response time between channels.

## Main Results

The Kaplan–Meier curves indicated that the probability of receiving a response is higher in the first days after the request and decreases over time.

The results showed differences between communication channels. Requests made through the Internet had a median response time approximately 45% higher than in-person requests, while requests made through WhatsApp were approximately 11% faster than in-person requests.

These findings suggest that the channel used to submit a request is statistically associated with the response time.

## Tools

- R
- survival
- flexsurv
- ggplot2
- ggfortify

## Reference

Nasu, V. H., da Silva, B. G., Borges, Y. M., & Melo, B. A. R. (2022).  
Da origem ao desfecho da solicitação: análise de sobrevivência aplicada ao contexto de acesso à informação pública.  
*Race, 21*(3), 361–392.  
https://doi.org/10.18593/race.29594
