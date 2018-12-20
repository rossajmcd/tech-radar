# Bulk data load via files

## Context

In the past, many legacy systems (and most large organisations, were based upon a batch process of data load. Usually via a regular feed, be it daily or weekly or monthly. This would involve a number of offline and back office processes, some manual, some slow. This was necessary due to the infrastructure and frameworks that existed at the time and the resiliency needs that could only be achieved through this methodology. Also, the need for a real-time, online process was not so high when these systems were first devised. Paper submissions or paper-based submissions were still the norm and a process that required scanning in documents that were handled asynchronously was required......therefore, this sort of batch processing overnight made sense.

The files would usually take the form of a delimited file format, whether that was more commonly CSV or less common versions. Sometimes these were simply structured formats of some sort.

Due to the fact that this is an approach that has existed for many years now, it can still be the default approach taken in designs. This approach must now be seen as an anti-pattern to be avoided.

## Problem

Bulk data file upload techniques cause the following issues:

* No real time feedback on the data being uploaded
* Tougher exception handling and reporting
* More complex code, leading to less maintainable code
* No real time risking - leading to more manual intervention
* Tighter coupling - with file formats such as CSV the order of the fields becomes paramount, as well as the general structure. Backwards compatibility is almost impossible.
* More infrastructure, leading to greater support and maintenance costs.
* Slower information gathering - the organisation needs to wait for the regular feed before receiving information as opposed to (potentially) real-time updates
* The cost of development sits mainly with the organisation and is not shared with vendors

## Solution

Almost invariably a single record API with a [standard message format](../../internal-advice/design-guidelines/microservice-message-format.md) is a better solution. It provides greater flexibility, can be delivered far more quickly, can be tested more effectively, can provide real time feedback and risking and is more extensible. The organisation can receive real updates from 3rd parties.......though still giving the flexibility to these 3rd parties to call the APIs in batch if they really need to. It also follows the same pattern that exists everywhere else on the platform.

## Example

## Exceptions
