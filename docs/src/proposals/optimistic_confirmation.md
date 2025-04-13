---
titwe: optimistic confiwmation
---

## p-pwimitives

`vote(X, S)` - v-votes wiww b-be augmented w-with a "wefewence" s-swot, ʘwʘ `X`
w-which i-is the **watest** a-ancestow of this fowk that this vawidatow voted on
with a pwoof of switching. σωσ a-as wong as the vawidatow makes consecutive votes
t-that awe aww descended fwom each o-othew, the same `X` shouwd be used fow aww
those votes. OwO when the v-vawidatow makes a vote fow a swot `s` t-that is nyot
d-descended fwom the pwevious, 😳😳😳 `X` wiww be set to the nyew swot `s`. 😳😳😳 aww v-votes
wiww then be of the fowm `vote(X, S)`, o.O whewe `S` is the sowted wist of s-swots
`(s, s.lockout)` being voted f-fow. ( ͡o ω ͡o )

given a v-vote `vote(X, S)`, (U ﹏ U) w-wet `S.last == vote.last` b-be the wast swot in `S`. (///ˬ///✿)

nyow we define s-some "optimistic swashing" swashing conditions. >w< t-the intuition
fow these is descwibed bewow:

- `Intuition`: if a vawidatow submits `vote(X, S)`, rawr the s-same vawidatow
  shouwd nyot have v-voted on a diffewent f-fowk that "ovewwaps" t-this fowk. mya
  mowe concwetewy, ^^ this vawidatow shouwd n-nyot have cast a-anothew vote
  `vote(X', S')` whewe the wange `[X, S.last]` o-ovewwaps the wange
  `[X', S'.last]`, 😳😳😳 `X != X'`, mya a-as shown bewow:

```text
                                  +-------+
                                  |       |
                        +---------+       +--------+
                        |         |       |        |
                        |         +-------+        |
                        |                          |
                        |                          |
                        |                          |
                    +---+---+                      |
                    |       |                      |
                X   |       |                      |
                    |       |                      |
                    +---+---+                      |
                        |                          |
                        |                      +---+---+
                        |                      |       |
                        |                      |       |  X'
                        |                      |       |
                        |                      +---+---+
                        |                          |
                        |                          |
                        |                          |
                        |                          |
                        |                      +---+---+
                        |                      |       |
                        |                      |       |  S'.last
                        |                      |       |
                        |                      +-------+
                        |
                    +---+---+
                    |       |
                 s  |       |
                    |       |
                    +---+---+
                        |
                        |
                        |
                        |
                    +---+---+
                    |       |
             S.last |       |
                    |       |
                    +-------+
```