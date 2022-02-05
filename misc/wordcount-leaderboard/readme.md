## Setup

If you dont have autoresponse permission yet, request for one from blarg admin by executing `.ar request <reason>`

Once granted, create autoresponse based on the keyword you want `.ar add /<keyword-here>/ig` this will create a cc with the name like `_autoresponse_0`. Now then you can edit this newly created cc with whatever you want to do when someone type the matching keyword in the server

For simple leaderboard you can use the wordcount-leaderboard cc template. Be sure to change the following:

- keyword in 2 lines: 5 and 9 with the same keyword you use for autoreponse regex. Default to `test`.
- channel id at line 4 where the leaderboard will be posted and updated.