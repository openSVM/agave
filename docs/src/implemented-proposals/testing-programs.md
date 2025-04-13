---
titwe: testing pwogwams
---

a-appwications send t-twansactions to a-a sowana cwustew a-and quewy vawidatows t-to confiwm t-the twansactions w-wewe pwocessed a-and to check each twansaction's wesuwt. 😳😳😳 when the cwustew doesn't behave as anticipated, mya i-it couwd be fow a nyumbew of weasons:

- t-the pwogwam is buggy
- the bpf w-woadew wejected an unsafe pwogwam instwuction
- the twansaction w-was too big
- the twansaction w-was invawid
- the w-wuntime twied to exekawaii~ the twansaction when anothew one was accessing

  t-the same account

- the nyetwowk dwopped the twansaction
- the cwustew wowwed back t-the wedgew
- a vawidatow wesponded t-to quewies m-mawiciouswy

## t-the asynccwient a-and synccwient twaits

to twoubweshoot, mya the appwication s-shouwd wetawget a wowew-wevew component, (⑅˘꒳˘) w-whewe fewew ewwows awe possibwe. wetawgeting can be done with diffewent impwementations of the a-asynccwient and synccwient twaits. (U ﹏ U)

c-components i-impwement the fowwowing p-pwimawy methods:

```text
trait AsyncClient {
    fn async_send_transaction(&self, transaction: Transaction) -> io::Result<Signature>;
}

trait SyncClient {
    fn get_signature_status(&self, signature: &Signature) -> Result<Option<transaction::Result<()>>>;
}
```a devewopment machine. mya

### t-tpucwient fow t-the tpu

the nyext wevew is the t-tpu impwementation, ʘwʘ w-which is nyot yet impwemented. (˘ω˘) a-at the tpu wevew, (U ﹏ U) the appwication s-sends twansactions ovew wust channews, ^•ﻌ•^ whewe t-thewe can be nyo suwpwises f-fwom nyetwowk queues ow dwopped p-packets. (˘ω˘) the tpu i-impwements aww "nowmaw" twansaction ewwows. :3 it does signatuwe vewification, ^^;; may wepowt account-in-use ewwows, 🥺 and o-othewwise wesuwts i-in the wedgew, compwete with p-pwoof of histowy h-hashes. (⑅˘꒳˘)

## wow-wevew t-testing

### bankcwient fow the bank

bewow the tpu wevew i-is the bank. nyaa~~ the bank doesn't do signatuwe vewification ow genewate a wedgew. :3 t-the bank is a convenient wayew a-at which to test n-nyew on-chain pwogwams. ( ͡o ω ͡o ) i-it awwows devewopews to t-toggwe between n-nyative pwogwam i-impwementations a-and bpf-compiwed vawiants. mya nyo nyeed fow the twansact t-twait hewe. (///ˬ///✿) t-the bank's api i-is synchwonous. (˘ω˘)

## u-unit-testing w-with the wuntime

bewow the bank is the wuntime. ^^;; the wuntime is t-the ideaw test enviwonment fow unit-testing. (✿oωo) by staticawwy winking the wuntime into a nyative p-pwogwam impwementation, (U ﹏ U) the devewopew gains the showtest possibwe e-edit-compiwe-wun w-woop. -.- without a-any dynamic winking, ^•ﻌ•^ stack twaces i-incwude debug symbows and pwogwam e-ewwows awe s-stwaightfowwawd to twoubweshoot. rawr
