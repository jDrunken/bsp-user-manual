<!-- TOC -->

# OpsNow manual build system  

## Gulp.js를 이용한 유지보수/확장

Gulp.js를 사용합니다. (ver :: 3.9.1)  

개별 플러그인에 대한 설명은 각 플러그인의 github 저장소를 참조하세요. 

Pandoc markdown + sass + jquery를 이용해 서비스에 배포되는 아웃풋을 만듭니다. 
멀지 않은 시간 내 pdf로 출력할 수 있는 기능을 만들 예정입니다. 

태스크 추가 시 Markdown \> html로 변환하는 과정이나, 트랜스파일 전 종착지(dist)를 깔끔하게 하는 등 반드시 동기화로 태스크가 진행되는 경우가 있으므로 이를 주의해 태스크 순서와 동작을 지정해 주시면 됩니다. 

스타일은 sass로 구성되어 있습니다. 각 섹션별로 파일이 쪼개져 있고, `manual.css`로 최종 빌드됩니다. 

`/source/_resource/template` 중 Html탬플릿은 pandoc markdown에서 참조하여 마크다운을 html 파일로 변환하는데 사용됩니다. 




## parsing type을 변경하게 되면...

지금은 **pandoc markdown**으로 파싱하고 있지만, 향후 parser를 **multi markdown** 이나 **GFM(github flavored markdown), commomMARK** 등으로 변경하게 되면 `gulpfile.js`에서 markdown to html을 변경하는 코드 중 from format을 변경해주세요.

```

//pandoc markdown을 사용할 경우

.pipe(pandoc({
    from:'markdown+hard_line_breaks+link_attributes+raw_html+table_captions',
    ....


// gfm을 사용할 경우
.pipe(pandoc({
    from:'gfm',
    ....


// commommark를 사용할 경우
.pipe(pandoc({
    from:'commonmark',
    ....


```

좀 더 자세한 옵션은 [https://pandoc.org/MANUAL.html#general-options](https://pandoc.org/MANUAL.html#general-options) 를 참고해 주세요.
