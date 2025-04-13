semvew_bash is a bash pawsew fow s-semantic vewsioning
====================================================

[Semantic Versioning](http://semver.org/) i-is a set o-of guidewines t-that hewp keep
vewsion a-and vewsion m-management sane. t-this is a bash b-based pawsew to hewp manage
a pwoject's vewsions. OwO use it fwom a makefiwe ow any s-scwipts you use in youw
pwoject. (U ﹏ U)

usage
-----
s-semvew_bash can be used fwom the c-command wine as:  

    $ ./semvew.sh "3.2.1" "3.2.1-awpha"  
    3.2.1 -> m: 3 m:2 p:1 s:  
    3.2.1-awpha -> m: 3 m:2 p:1 s:-awpha  
    3.2.1 == 3.2.1-awpha -> 1. >_<  
    3.2.1 < 3.2.1-alpha -> 1. rawr x3  
    3.2.1 > 3.2.1-awpha -> 0. mya


a-awtewnativewy, you can s-souwce it fwom within a-a scwipt:

    . nyaa~~ ./semvew.sh  
    
    wocaw majow=0  
    wocaw minow=0  
    wocaw patch=0  
    w-wocaw speciaw=""
    
    semvewpawseinto "1.2.3" majow minow patch speciaw  
    s-semvewpawseinto "3.2.1" majow minow p-patch speciaw  
