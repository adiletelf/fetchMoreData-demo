## fetchMoreData Demo
This project is used to demonstrate how to use PowerBI [fetchMoreData](https://learn.microsoft.com/en-us/power-bi/developer/visuals/fetch-more-data) functionality.
Specifically, there seems to be a bug in the way fetchMoreData works when user switches pages.

## Steps to reproduce the bug
1. Open attached report (it's not here for confidentiality reasons).
2. The visual loads all data with 3 fetches (Create, Append, Append).
3. Switch to another page. Then switch back.
4. Use native slicer to change the data role "Metric" to another value.
This will cause the visual to load data once more.
5. Observe console. Notice how `updateId` is not consistent. There are multiple updates with `Create` kind.
There seems to be some race condition for loading the data.
6. With the race condition some data was sent to another update (lost). The visual now display incomplete data.