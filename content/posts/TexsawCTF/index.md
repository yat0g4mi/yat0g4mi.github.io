--- 
title: "Texsaw CTF"
date: 2024-03-25T17:31:00+07:00
tags: [forensics, osint]
author : [1]
---

Cre image: [warlock smurf](https://warlocksmurf.github.io/$whoami/)
## 1. Osint/Geo-Location 
- Challenge :

    ![pic1](https://live.staticflickr.com/65535/54180858629_abe4565647_b.jpg)
- PNG file: 

    ![pic2](https://live.staticflickr.com/65535/54181006255_ea9e258213_b.jpg)
- Using GG image and focusing on the large building in the photo, we can see a number of matching images.

    ![pic3](https://live.staticflickr.com/65535/54180858639_fa12d91640_b.jpg)
-  I later identified it as the ```TCC Legacy Kincaid building```. Check GG map and you will see it matches the image. It is located on Legacy Street,Texas.

FLAG: `texsaw{LEGACY_DRIVE}`

## 2. Forensics/The Forked Cave
- Challenge:

    ![pic4](https://live.staticflickr.com/65535/54179683942_31b94c6f10_b.jpg)
- The challenge gives us a git directory. Because I've done a similar challenge before, I used ```git log``` to check:

    ![pic5](https://live.staticflickr.com/65535/54180840113_d503dd622d_b.jpg)
- And using command : ```git diff 02589c89210a9718a03992eec1a7da85e15c7c7d 9c6d7b5d77ba2f73fca83d026de1fe7904ce6e0b```, we get the flag:

    ![pic6](https://live.staticflickr.com/65535/54180568836_f520790e65_o.png)

FLAG: `texsaw{git_g00d_or_git_d3ath}`

## 3. Forensics/PS2 games 
- Challenge : 

    ![pic7](https://live.staticflickr.com/65535/54180860269_463cb30896_b.jpg)
- My initial idea was to use code to filter out all games between ```2000-2009```, then check their ```platform-id```. But after solving the challenge that way, I tried ```Workbench``` and it was much simpler. Just with the following SQL code:

```sql
SELECT COUNT(DISTINCT Games.game_id) AS num_games
FROM Games
JOIN GamePlatforms ON Games.game_id = GamePlatforms.game_id
JOIN Platforms ON GamePlatforms.platform_id = Platforms.platform_id
WHERE Platforms.platform_name = 'Playstation'
AND YEAR(Games.release_date) BETWEEN 2000 AND 2009;
```

FLAG: `texsaw{42}`

## 4. Crypto/Freaky Flags
- Challenge :

    ![pic8](https://live.staticflickr.com/65535/54181005545_d97da9d23f_b.jpg)
- PNG file:

    ![pic9](https://live.staticflickr.com/65535/54180837763_0b34188948_b.jpg)
- Luckily, I had just learned HTML and used [Color Identity](https://redketchup.io/color-picker) to determine the color of an image, so I immediately thought of trying it out. Each color will have 3 RGB values and I try to put them into ASCII decode. It works and I get the flag.

    ![pic10](https://live.staticflickr.com/65535/54180837783_a8324a5bea_b.jpg)

FLAG: `texsaw{the_flag_is_the_flag!}`

## 5. Osint/TrickyTree
- A challenge that I initially thought I would give up on. But when there were about 5-6 hours left in the competition, I tried again. And this time thanks to the predecessors of the challenge, I have [this link](https://www.familytreenow.com/trees/715273) :

    ![pic11](https://live.staticflickr.com/65535/54181008175_22fe450eee_o.png)
- But guess what, of course it's not that easy. I tried using a wayback machine but it didn't work very well. Suddenly I thought of a website I used from the ```0xL4ugh tournament```, which is ```Archive.Today```. I tried copying the link I just received and got the results:

    ![pic12](https://live.staticflickr.com/65535/54181008180_5db99cecdb_b.jpg)
- Click to see and we will see his father's name. View profile and get date of birth.Thank all players who went first.

    ![pic13](https://live.staticflickr.com/65535/54181008170_1da8f074ed_o.png)

FLAG: `texsaw{09_02_1985}`

## 6. Forensics/Market Data
- Challenge :

    ![pic14](https://live.staticflickr.com/65535/54180839863_7b10e56a6e_b.jpg)
- I use the following SQL code to filter and get the correct results:

    ```sql
    SELECT 
        SUM(revenue) AS total_revenue
    FROM (
        SELECT 
            od.game_id,
            SUM(od.quantity * od.subtotal) AS revenue,
            ROW_NUMBER() OVER (ORDER BY SUM(od.quantity * od.subtotal) DESC) AS revenue_rank
        FROM 
            OrderDetails od
        JOIN 
            Games g ON od.game_id = g.game_id
        JOIN 
            Genres ge ON g.genre_id = ge.genre_id
        JOIN 
            Orders o ON od.order_id = o.order_id
        WHERE 
            ge.genre_name = 'Action' -- Filter by Action genre
            AND YEAR(o.order_date) = 2023 -- Filter orders from 2023
        GROUP BY 
            od.game_id
    ) AS revenue_by_game
    WHERE 
        revenue_rank = 5; -- Select the 5th ranked game's revenue
    ```

FLAG: `texsaw{247.16}`

![meme](https://media.tenor.com/wT-64avQxegAAAAi/i-love-you-pepe.gif)