# 词性
词性指以词的特点作为划分词类的根据。现代汉语的词可以分为两类14种词性。
# 常见词性分类
词性分类又叫词性标注(Part-Of-Speech tag, POS-tag),常见的词性标准类型如下：

1. 名词
	- n 名词
	- nr 人名
	- nr1 汉语姓氏
	- nr2 汉语名字
	- nrj 日语人名
	- nrf 音译人名
	- ns 地名
	- nsf 音译地名
	- nt 机构团体名
	- nz 其它专名
	- nl 名词性惯用语
	- ng 名词性语素

2. 时间词
	- t 时间词
	- tg 时间词性语素

3. 处所词
	- s 处所词 (在公司，在学校)

4. 方位词
	- f 方位词

5. 动词
	- v 动词
	- vd 副动词
	- vn 名动词
	- vshi 动词“是”
	- vyou 动词“有”
	- vf 趋向动词
	- vx 形式动词
	- vi 不及物动词（内动词）
	- vl 动词性惯用语
	- vg 动词性语素

6. 形容词
	- a 形容词
	- ad 副形词
	- an 名形词
	- ag 形容词性语素
	- al 形容词性惯用语

7. 区别词
	- b 区别词 
	- bl 区别词性惯用语

8. 状态词
	- z 状态词

9. 代词
	- r 代词
	- rr 人称代词
	- rz 指示代词
	- rzt 时间指示代词
	- rzs 处所指示代词
	- rzv 谓词性指示代词
	- ry 疑问代词
	- ryt 时间疑问代词
	- rys 处所疑问代词
	- ryv 谓词性疑问代词
	- rg 代词性语素

10. 数词
	- m 数词
	- mq 数量词

11. 量词
	- q 量词
	- qv 动量词
	- qt 时量词

12. 副词
	- d 副词

13. 介词
	- p 介词
	- pba 介词“把”
	- pbei 介词“被”

14. 连词
	- c 连词
	- cc 并列连词

# 使用Jieba词性分类
Jieba下进行词性分类非常简便。

    seg_lig = jieba.posseg.cut(text)
    for w,tag in seg_lig:
        print "%s /%s" % (w,tag)

以经典句子为例，“我爱北京天安门“，词性分类的结果为：

	我 /r
	爱 /v
	北京 /ns
	天安门 /ns

使用一个稍微复杂的例子。

>
据半岛电视台援引叙利亚国家电视台称，叙利亚已经对美国、英国、法国的空袭进行了反击。据介绍，在叙军武器库中，对西方最具威慑力的当属各型战术地对地弹道导弹。尽管美英法是利用巡航导弹等武器发动远程空袭，但叙军要对等还击却几乎是“不可能完成的任务”。目前叙军仍能作战的战机仍是老旧的苏制米格-29、米格-23、米格-21战斗机和苏-22、苏-24轰炸机
	
	
由于文字较多，使用分行显示会十分乱，我们稍微修改代码，让分词后的词性标注结果紧跟着原单词。

    seg_lig = jieba.posseg.cut(text)
    print " ".join(["%s /%s" % (w,tag) for w,tag in seg_lig])

分词的结果如下所示。

>
>据 /p 半岛 /n 电视台 /n 援引 /vn 叙利亚 /ns 国家 /n 电视台 /n 称 /v ， /x 叙利亚 /ns 已经 /d 对 /p 美国 /ns 、 /x 英国 /ns 、 /x 法国 /ns 的 /uj 空袭 /v 进行 /v 了 /ul 反击 /v 。 /x 据介绍 /n ， /x 在 /p 叙军 /n 武器库 /n 中 /f ， /x 对 /p 西方 /s 最 /d 具 /v 威慑力 /n 的 /uj 当属 /n 各型 /r 战术 /n 地对地 /n 弹道导弹 /n 。  
	 尽管 /c 美英 /nz 法 /j 是 /v 利用 /n 巡航导弹 /n 等 /u 武器 /n 发动 /vn 远程 /n 空袭 /v ， /x 但 /c 叙军 /n 要 /v 对 /p 等 /u 还击 /v 却 /d 几乎 /d 是 /v “ /x 不 /d 可能 /v 完成 /v 的 /uj 任务 /n ” /x 。 /x 目前 /t 叙军 /n 仍 /d 能 /v 作战 /v 的 /uj 战机 /n 仍 /d 是 /v 老 /a 旧 /a 的 /uj 苏制 /n 米格 /nrt - /x 29 /m 、 /x 米格 /nrt - /x 23 /m 、 /x 米格 /nrt - /x 21 /m 战斗机 /n 和 /c 苏 /ns - /x 22 /m 、 /x 苏 /j - /x 24 /m 轰炸机 /n ， /x 它们 /r 在 /p 现代化 /vn 的 /uj 西方 /s 空军 /n 面前 /f 难 /a 有 /v 自保 /vn 之 /u 力 /n ， /x 因此 /c 叙军 /n 的 /uj 远程 /n 反击 /v 只能 /v 依靠 /v 另 /r 一个 /m 撒手锏 /n — /x — /x 地对地 /n 战术 /n 弹道导弹 /n 。
	

# 参考文献

- https://www.cnblogs.com/csj007523/p/7773027.html
