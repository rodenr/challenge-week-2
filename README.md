# Name

Ryan Roden

# How many points have you earned?

100/100

(Make your own calculation and replace the number 0 with the points you think you've earned.)

# Show and tell (10 points)

[Fire Breathing Animetronic Pony](http://www.instructables.com/id/Make-a-Fire-Breathing-Animetronic-Pony-from-FurRea/)

# Checkpoints

## Checkpoint 1 (5 points)

![image](http://i.imgur.com/48af9zE.png)

## Checkpoint 2 (5 points)

![image](http://i.imgur.com/08UqF5g.png)

## Checkpoint 3 (5 points)

![image](http://i.imgur.com/VOcWFOP.png)

## Checkpoint 4 (5 points)

![image](http://i.imgur.com/Saqfp87.png)

## Study Questions (3 points x 4 = 12 points)

### Q1. (3 points)

the www1 through www3 are assigned names for hosts for the splunk server.  There are more than one for load balancing as to not overstress a single server.

### Q2. (3 points)

If everything worked properly for a purchase the status is 200, so a status that isn't 200 is not a successful purchase.

### Q3. (3 points)

The heavy use of the pipe would be to channel data from the previous query into the query following the |

### Q4. (3 points)

depending on the scale of the site, a structural database might not support something like that in real time.

# Challenges

## Challenge 1-a (2 points)
```
sourcetype=access_* | stats count
```
![image](http://i.imgur.com/KVEMpqB.png)

## Challenge 1-b (2 points)
```
sourcetype=access_* | stats count as "Events"
```
![image](http://i.imgur.com/rYRHDqK.png)

## Challenge 1-c (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS "Purchases"
```
![image](http://i.imgur.com/NNC09WH.png)

## Challenge 1-d (2 points)
```
sourcetype=access_* | stats count AS "Events", count(eval(action="purchase")) AS "Purchases", count(eval(action="addtocart")) AS "AddToCarts", count(eval(action="remove")) AS "Removes"
```
![image](http://i.imgur.com/RJTJOM0.png)

## Challenge 1-e (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/r4DT2HG.png)

## Challenge 1-f (2 points)
```
sourcetype=access_* | stats max(bytes)
```
![image](http://i.imgur.com/r4DT2HG.png)

## Challenge 1-g (2 points)
```
sourcetype=access_* | stats max(bytes) as  MAX
```
![image](http://i.imgur.com/ZTzmbW6.png)

## Challenge 1-h (2 points)
```
sourcetype=access_* | stats max(bytes) as  MAX, min(bytes), avg(bytes)
```
![image](http://i.imgur.com/guku7nF.png)

## Challenge 1-i (2 points)
```
sourcetype=access_* | stats distinct_count(productId), values(productId) as "UniqueProducts"
```
![image](http://i.imgur.com/wINDPxB.png)


## Challenge 2-a (2 points)
```
sourcetype=access_* productId cart.do | top clientip
```
![image](http://i.imgur.com/CKLKXmo.png)

## Challenge 2-b (2 points)
```
sourcetype=access_* productId cart.do | top date_wday | head 3
```
![image](http://i.imgur.com/0zEQFCN.png)

## Challenge 2-c (2 points)
```
sourcetype=access_* productId cart.do | top productId
```
![image](http://i.imgur.com/iCivo6Q.png)


## Challenge 2-d (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday | top productId
```
![image](http://i.imgur.com/JpsjuM8.png)

## Challenge 2-e (2 points)
```
sourcetype=access_* productId cart.do date_wday=friday action=purchase | top productId
```
![image](http://i.imgur.com/DdFZ8Sf.png)

## Challenge 2-f (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top productId limit=1
```
![image](http://i.imgur.com/HIkCfaK.png)

## Challenge 2-g (2 points)
```
sourcetype=access_* productId cart.do action=purchase | top productId by date_wday limit=1
```
![image](http://i.imgur.com/hbosOZC.png)

## Challenge 3-a (2 points)
```
sourcetype=access_* productId=* | timechart count
```
![image](http://i.imgur.com/2hnXf44.png)

## Challenge 3-b (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip)
```
![image](http://i.imgur.com/zdequi9.png)

## Challenge 3-c (2 points)
```
sourcetype=access_* productId=* | timechart distinct_count(clientip) span=hours
```
![image](http://i.imgur.com/agesizx.png)

## Challenge 3-d (2 points)
```
sourcetype=access_* productId=* | timechart count by host
```
![image](http://i.imgur.com/iMzXgzC.png)

## Challenge 3-e (2 points)
```
sourcetype=access_* productId=* | timechart count by productId
```
![image](http://i.imgur.com/nz7K5QW.png)

## Challenge 3-f (2 points)
```
sourcetype=access_* productId=* | timechart count by productId useother=false usenull=false limit=16
```
![image](http://i.imgur.com/vbf9bU7.png)

## Challenge 3-g (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip
```
![image](http://i.imgur.com/kLra7Tt.png)

## Challenge 3-h (2 points)
```
sourcetype=access_* productId=* | timechart count by clientip useother=false
```
![image](http://i.imgur.com/H1DnT05.png)

## Challenge 3-i (2 points)
```
sourcetype=access_* productId=* | timechart sum(bytes) span=hours
```
![image](http://i.imgur.com/FxQ6keO.png)

## Challenge 4-a (4 points)
```
sourcetype=access_* | rex "(?<mymethod>GET)" | table mymethod, method, _raw |  rex "(?<mymethod>POST)" | table mymethod, method, _raw
```
![image](http://i.imgur.com/FNm4dfG.png)

## Challenge 4-b (4 points)
```
sourcetype=access_* action | rex "(GET|POST) /cart.do\?action=(?<myaction>(purchase|addtocart|remove|view|remove|purchase|changequantity))" | table myaction, action, _raw
```
![image](http://i.imgur.com/sQqsl22.png)
