# Useful commands

## DESC

describe table- sort of like show, but can apply other things to it.

## AS

aliasing - doesn't alter the table, but labels the data differently (good for joining)

## DELETE

Removes data, if `DELETE FROM <TABLE>` is ran it will empty the table, but is not the same as dropping a table

## Replace

Replaces param A with param B

`SELECT REPLACE(CONCAT('I', ' ', 'like', ' ', 'cats'), ' ', '-');`

## Distinct

Returns unique data, can combine multiple columns (first name last name to return unique people without getting rid of people who share one of the columns)

## Order by *number*

orders by that param from the select statement
