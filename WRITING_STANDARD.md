# Writing Standard

## 文件结构
所有手稿文件在手稿目录`/manuscript`文件夹下

按照ECMA-262文档的目录结构, 分为两层:  

1. 大章节如: "1 Scope", "2 Conformance"
2. 小章节如: "4.1 Web Scripting", "5.2 Algorithm Conventions"

因此, 文件结构设计如下:

- 如大章节没有包含小章节(如"1 Scope"), 则直接放置在手稿目录下, 文件名格式为`[章节号]_[章节名称].md`, 其中`章节名称`即ECMA-262文档中的章节名称, 但空格被下划线`_`替换。如`/manuscript/1_scope.md`, `/manuscript/2_conformance.md`
- 如大章节包含小章节, 则在手稿目录下创建对应的子文件夹, 文件夹名格式为`[章节号]_[章节名称]`, `[章节名称]`规则和之前相同。如`/manuscript/4_overview/`
- 小章节的手稿文件创建在对应的大章节文件夹下, 文件名格式为`[章节号]_[章节名称].md`, `[章节名称]`规则和之前相同, `[章节号]`即ECMA-262文档中的章节号, 但点号`.`被下划线`_`替换。如`/manuscript/4_overview/4_1_web_scripting.md`
