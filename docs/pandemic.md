# The pandemic

The total number of cases of the pandemic found with this query:

**SPARQL** [sparql/earthAllCasesToday.rq](sparql/earthAllCasesToday.code.html) ([run](https://query.wikidata.org/embed.html#SELECT%20%3FnumberOfCases%20%20WHERE%20%7B%0A%20%20wd%3AQ81068910%20wdt%3AP1603%20%3FnumberOfCases%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A), [edit](https://query.wikidata.org/#SELECT%20%3FnumberOfCases%20%20WHERE%20%7B%0A%20%20wd%3AQ81068910%20wdt%3AP1603%20%3FnumberOfCases%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%0A))

```sparql
SELECT ?numberOfCases  WHERE {
  wd:Q81068910 wdt:P1603 ?numberOfCases .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```

Which gives us:

<table>
  <tr>
    <td><b>numberOfCases</b></td>
  </tr>
  <tr>
    <td>153517</td>
  </tr>
</table>

## Progression

However, we may be more interested in the number of cases over time.
Then we need a more complex query suitable for statement qualifiers:

**SPARQL** [sparql/earthAllCases.rq](sparql/earthAllCases.code.html) ([run](https://query.wikidata.org/embed.html#SELECT%20%3Fdate%20%3FnumberOfCases%20WHERE%20%7B%0A%20%20wd%3AQ81068910%20p%3AP1603%20%3FnumberOfCasesStat%20.%0A%20%20%3FnumberOfCasesStat%20ps%3AP1603%20%3FnumberOfCases%20%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20pq%3AP585%20%3Fdate%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%20ORDER%20BY%20ASC%28%3Fdate%29%0A), [edit](https://query.wikidata.org/#SELECT%20%3Fdate%20%3FnumberOfCases%20WHERE%20%7B%0A%20%20wd%3AQ81068910%20p%3AP1603%20%3FnumberOfCasesStat%20.%0A%20%20%3FnumberOfCasesStat%20ps%3AP1603%20%3FnumberOfCases%20%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20pq%3AP585%20%3Fdate%20.%0A%20%20SERVICE%20wikibase%3Alabel%20%7B%20bd%3AserviceParam%20wikibase%3Alanguage%20%22%5BAUTO_LANGUAGE%5D%2Cen%22.%20%7D%0A%7D%20ORDER%20BY%20ASC%28%3Fdate%29%0A))

```sparql
SELECT ?date ?numberOfCases WHERE {
  wd:Q81068910 p:P1603 ?numberOfCasesStat .
  ?numberOfCasesStat ps:P1603 ?numberOfCases ;
                     pq:P585 ?date .
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
} ORDER BY ASC(?date)
```

This gives us this time series:

<table>
  <tr>
    <td><b>date</b></td>
    <td><b>numberOfCases</b></td>
  </tr>
  <tr>
    <td>2020-01-20T00:00:00Z</td>
    <td>282</td>
  </tr>
  <tr>
    <td>2020-01-21T00:00:00Z</td>
    <td>314</td>
  </tr>
  <tr>
    <td>2020-01-23T00:00:00Z</td>
    <td>581</td>
  </tr>
  <tr>
    <td>2020-01-24T00:00:00Z</td>
    <td>846</td>
  </tr>
  <tr>
    <td>2020-01-25T00:00:00Z</td>
    <td>1320</td>
  </tr>
  <tr>
    <td>2020-01-26T00:00:00Z</td>
    <td>2014</td>
  </tr>
  <tr>
    <td>2020-01-27T00:00:00Z</td>
    <td>2798</td>
  </tr>
  <tr>
    <td>2020-01-28T00:00:00Z</td>
    <td>4596</td>
  </tr>
  <tr>
    <td>2020-01-29T00:00:00Z</td>
    <td>6065</td>
  </tr>
  <tr>
    <td>2020-01-30T00:00:00Z</td>
    <td>7818</td>
  </tr>
  <tr>
    <td>2020-01-31T00:00:00Z</td>
    <td>9826</td>
  </tr>
  <tr>
    <td>2020-02-01T00:00:00Z</td>
    <td>11953</td>
  </tr>
  <tr>
    <td>2020-02-02T00:00:00Z</td>
    <td>14557</td>
  </tr>
  <tr>
    <td>2020-02-03T00:00:00Z</td>
    <td>17391</td>
  </tr>
  <tr>
    <td>2020-02-04T00:00:00Z</td>
    <td>20630</td>
  </tr>
  <tr>
    <td>2020-02-05T00:00:00Z</td>
    <td>24554</td>
  </tr>
  <tr>
    <td>2020-02-06T00:00:00Z</td>
    <td>28276</td>
  </tr>
  <tr>
    <td>2020-02-07T00:00:00Z</td>
    <td>31481</td>
  </tr>
  <tr>
    <td>2020-02-08T00:00:00Z</td>
    <td>34886</td>
  </tr>
  <tr>
    <td>2020-02-09T00:00:00Z</td>
    <td>37558</td>
  </tr>
  <tr>
    <td>2020-02-10T00:00:00Z</td>
    <td>40554</td>
  </tr>
  <tr>
    <td>2020-02-11T00:00:00Z</td>
    <td>43103</td>
  </tr>
  <tr>
    <td>2020-02-12T00:00:00Z</td>
    <td>45171</td>
  </tr>
  <tr>
    <td>2020-02-13T00:00:00Z</td>
    <td>46997</td>
  </tr>
  <tr>
    <td>2020-02-13T00:00:00Z</td>
    <td>60329</td>
  </tr>
  <tr>
    <td>2020-02-14T00:00:00Z</td>
    <td>49053</td>
  </tr>
  <tr>
    <td>2020-02-14T00:00:00Z</td>
    <td>64437</td>
  </tr>
  <tr>
    <td>2020-02-15T00:00:00Z</td>
    <td>50580</td>
  </tr>
  <tr>
    <td>2020-02-15T00:00:00Z</td>
    <td>67102</td>
  </tr>
  <tr>
    <td>2020-02-16T00:00:00Z</td>
    <td>69267</td>
  </tr>
  <tr>
    <td>2020-02-16T00:00:00Z</td>
    <td>51857</td>
  </tr>
  <tr>
    <td>2020-02-17T00:00:00Z</td>
    <td>71429</td>
  </tr>
  <tr>
    <td>2020-02-18T00:00:00Z</td>
    <td>73332</td>
  </tr>
  <tr>
    <td>2020-02-19T00:00:00Z</td>
    <td>75204</td>
  </tr>
  <tr>
    <td>2020-02-20T00:00:00Z</td>
    <td>75748</td>
  </tr>
  <tr>
    <td>2020-02-21T00:00:00Z</td>
    <td>76769</td>
  </tr>
  <tr>
    <td>2020-02-22T00:00:00Z</td>
    <td>77794</td>
  </tr>
  <tr>
    <td>2020-02-23T00:00:00Z</td>
    <td>78811</td>
  </tr>
  <tr>
    <td>2020-02-24T00:00:00Z</td>
    <td>79331</td>
  </tr>
  <tr>
    <td>2020-02-25T00:00:00Z</td>
    <td>80239</td>
  </tr>
  <tr>
    <td>2020-02-26T00:00:00Z</td>
    <td>81109</td>
  </tr>
  <tr>
    <td>2020-02-27T00:00:00Z</td>
    <td>82294</td>
  </tr>
  <tr>
    <td>2020-02-28T00:00:00Z</td>
    <td>83652</td>
  </tr>
  <tr>
    <td>2020-02-29T00:00:00Z</td>
    <td>85403</td>
  </tr>
  <tr>
    <td>2020-03-01T00:00:00Z</td>
    <td>87137</td>
  </tr>
  <tr>
    <td>2020-03-02T00:00:00Z</td>
    <td>88948</td>
  </tr>
  <tr>
    <td>2020-03-03T00:00:00Z</td>
    <td>90869</td>
  </tr>
  <tr>
    <td>2020-03-04T00:00:00Z</td>
    <td>93090</td>
  </tr>
  <tr>
    <td>2020-03-05T00:00:00Z</td>
    <td>95333</td>
  </tr>
  <tr>
    <td>2020-03-06T00:00:00Z</td>
    <td>98192</td>
  </tr>
  <tr>
    <td>2020-03-07T00:00:00Z</td>
    <td>101927</td>
  </tr>
  <tr>
    <td>2020-03-08T00:00:00Z</td>
    <td>105586</td>
  </tr>
  <tr>
    <td>2020-03-09T00:00:00Z</td>
    <td>109578</td>
  </tr>
  <tr>
    <td>2020-03-10T00:00:00Z</td>
    <td>113702</td>
  </tr>
  <tr>
    <td>2020-03-11T00:00:00Z</td>
    <td>118326</td>
  </tr>
  <tr>
    <td>2020-03-12T00:00:00Z</td>
    <td>125048</td>
  </tr>
  <tr>
    <td>2020-03-13T00:00:00Z</td>
    <td>132758</td>
  </tr>
  <tr>
    <td>2020-03-14T00:00:00Z</td>
    <td>142539</td>
  </tr>
  <tr>
    <td>2020-03-15T00:00:00Z</td>
    <td>153517</td>
  </tr>
</table>

