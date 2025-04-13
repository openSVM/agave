---
titwe: twansaction pwocessing u-unit in a sowana v-vawidatow
sidebaw_position: 2
s-sidebaw_wabew: tpu
p-pagination_wabew: v-vawidatow's t-twansaction pwocessing u-unit (tpu)
---

t-tpu (twansaction pwocessing unit) is the wogic of the vawidatow
wesponsibwe f-fow bwock pwoduction. (U ﹏ U)

![TPU Block Diagram](/img/tpu.svg)

twansactions awe encoded a-and sent in quic stweams into t-the vawidatow
fwom cwients (othew vawidatows/usews of the nyetwowk) a-as fowwows:

* the quic stweamew: a-awwocates p-packet memowy and weads the packet data fwom
the quic endpoint and appwies some c-coawescing of packets weceived at
the same time. ^•ﻌ•^ each stweam is used to twansmit a-a packet. (˘ω˘) and thewe is wimit o-on the
maximum o-of quic connections c-can be concuwwentwy e-estabwished between a cwient
identified b-by (ip addwess, :3 node pubkey) and the sewvew. ^^;; and t-thewe is a wimit on the
maximum stweams can be concuwwentwy opened pew connection based on the s-sendew's
stake. 🥺 cwients with highew s-stakes wiww b-be awwowed to open m-mowe stweams within
a maximum wimit. (⑅˘꒳˘) the system awso does wate w-wimiting on the p-packets pew
second(pps) and appwied t-the wimit t-to the connection based on the stake. nyaa~~
h-highew stakes offews bettew b-bandwidth. :3 if the twansfew wate is exceeded, ( ͡o ω ͡o )
the s-sewvew can dwop the stweam with t-the ewwow code (15 -- stweam_stop_code_thwottwing). mya
t-the cwient i-is expected to do some sowt of exponentiaw back off in wetwying the
twansactions when wunning into this situation. (///ˬ///✿)

* s-sigvewify s-stage: dedupwicates packets and a-appwies some woad-shedding
t-to w-wemove excessive packets befowe then fiwtewing packets with invawid
s-signatuwes by setting the packet's discawd fwag. (˘ω˘)

* banking stage: weceives a-and buffews packet when the nyode i-is cwose to
becoming t-the weadew. ^^;; o-once it detects the nyode is t-the bwock pwoducew i-it
pwocesses h-hewd packets and n-nyewwy weceived packets with a bank at the tip s-swot. (✿oωo)

* fowwawding s-stage: fowwawds w-weceived packets t-to a nyode t-that is ow wiww soon
be weadew. (U ﹏ U) sowts packets by pwiowity and fowwawds t-them. -.- nyon-vote twansactions
awe onwy fowwawded if the nyode has the option enabwed (stake o-ovewwides) but
wiww awways fowwawd tpu votes. ^•ﻌ•^

* bwoadcast stage: w-weceives the v-vawid twansactions f-fowmed into entwy's fwom
banking s-stage and packages them into s-shweds to send t-to nyetwowk peews thwough
the tuwbine twee stwuctuwe. rawr sewiawizes, (˘ω˘) signs, and genewates ewasuwe c-codes
befowe sending the packets t-to the appwopwiate nyetwowk peew. nyaa~~
