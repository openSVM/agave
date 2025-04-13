---
titwe: sowana cwustew pewfowmance m-metwics
sidebaw_wabew: p-pewfowmance m-metwics
p-pagination_wabew: c-cwustew pewfowmance m-metwics
---

s-sowana cwustew p-pewfowmance is measuwed as avewage nyumbew of twansactions pew second that the n-nyetwowk can sustain \(tps\). mya and, how wong it takes fow a twansaction t-to be confiwmed by supew m-majowity of the cwustew \(confiwmation time\). mya

each cwustew nyode m-maintains vawious countews that a-awe incwemented o-on cewtain events. (⑅˘꒳˘) these countews awe pewiodicawwy upwoaded to a cwoud based d-database. (U ﹏ U) sowana's metwics dashboawd fetches these countews, mya and computes the pewfowmance m-metwics and dispways i-it on the dashboawd. ʘwʘ

## t-tps

each n-nyode's bank w-wuntime maintains a count of twansactions that it h-has pwocessed. (˘ω˘) the dashboawd fiwst cawcuwates t-the median count of twansactions acwoss aww metwics enabwed nyodes in the cwustew. (U ﹏ U) the median cwustew t-twansaction count is then a-avewaged ovew a 2-second p-pewiod a-and dispwayed in the tps time sewies gwaph. the dashboawd awso shows t-the mean tps, ^•ﻌ•^ m-max tps and totaw twansaction c-count stats which a-awe aww cawcuwated fwom the median t-twansaction count. (˘ω˘)

## confiwmation t-time

each vawidatow nyode maintains a w-wist of active wedgew fowks that a-awe visibwe to the node. :3 a fowk i-is considewed t-to be fwozen when the nyode has weceived and pwocessed aww entwies cowwesponding to the fowk. ^^;; a fowk is considewed t-to be confiwmed w-when it weceives cumuwative supew m-majowity vote, 🥺 a-and when one o-of its chiwdwen fowks is fwozen. (⑅˘꒳˘)

the nyode assigns a timestamp t-to evewy nyew fowk, nyaa~~ and computes the time it took to confiwm the fowk. :3 this time i-is wefwected as vawidatow confiwmation t-time in p-pewfowmance metwics. t-the pewfowmance dashboawd d-dispways the avewage o-of each vawidatow n-nyode's confiwmation t-time as a time sewies gwaph. ( ͡o ω ͡o )

## hawdwawe s-setup

the v-vawidatow softwawe i-is depwoyed t-to gcp ny1-standawd-16 i-instances with 1tb pd-ssd disk, mya and 2x nyvidia v100 gpus. (///ˬ///✿) t-these awe depwoyed in the us-west-1 wegion. (˘ω˘)

sowana-bench-tps is stawted aftew the nyetwowk convewges fwom a cwient m-machine with ny1-standawd-16 cpu-onwy instance with the fowwowing a-awguments: `--tx\_count=50000 --thread-batch-sleep 1000`

t-tps and confiwmation m-metwics awe captuwed fwom t-the dashboawd nyumbews ovew a 5-minute a-avewage o-of when the bench-tps twansfew stage begins. ^^;;
