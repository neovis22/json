# json Library
주석 및 Trailing comma를 지원하는 json 라이브러리 입니다.

## Requirements
[Autohotkey v1.1.31+](https://www.autohotkey.com/)

## Installation
아래 두가지 방법중 하나를 선택하여 설치하세요. 먼저 [git](https://git-scm.com/download/win)이 설치되어 있어야 합니다.

오토핫키 스크립트로 설치하는 방법:
```ahk
; 표준 라이브러리에 설치
RunWait git clone https://github.com/neovis22/json.git, % a_ahkPath "\..\Lib"

; 로컬 라이브러리에 설치
RunWait git clone https://github.com/neovis22/json.git Lib/json
```

사용할 스크립트에 아래 코드를 추가하세요.
```ahk
#Include <json\json>
```

## Usage

#### Basic usage
```ahk
obj := json_parse(json) ; 객체로 변환

json := json_stringify(obj) ; json으로 변환
```

#### File
```ahk
json_dump("my.json", obj) ; 저장

obj := json_load("my.json") ; 불러오기
```
파일을 저장하거나 불러올 때 오류가 발생하면 예외를 `throw`합니다.

#### Constants
```ahk
arr := [json_true(), json_false(), json_null()]
json := json_stringify(arr)

MsgBox % json ; [true,false,null]
```
오토핫키에서는 `true`, `false`, `null` 타입을 구분하지 않으므로 타입을 구분하는 서버로 보낼 때는 별도의 함수로 대체합니다. 각 함수의 실제 리턴값은 고유한 객체이며 json으로 변환시 상수로 치환됩니다.

## Functions
- `json_load(path, encoding="utf-8")` json 파일 불러오기
- `json_dump(path, object, encoding="utf-8")` json 파일로 저장
- `json_parse(json)`
json을 객체로 변환
- `json_stringify(object)`
객체를 json으로 변환
- `json_pretty(object, space=4)`
`space`로 지정된 공백 수 혹은 문자열로 들여쓰기된 json으로 변환
- `json_true()`
json 으로 변환시 true로 변환
- `json_false()`
json 으로 변환시 false로 변환
- `json_null()`
json 으로 변환시 null로 변환
- `json_escape(str)`
- `json_unescape(str)`
- `json_setMaxReferenceCount(limit=300)`
재참조 최대 횟수를 지정
- `json_setEscapePattern(regex="[^\x{20}-\x{10ffff}]")`
`\uXXXX`형식으로 이스케이프 처리할 문자를 정규식으로 지정

## Features
- 숫자와 문자열 구분 (`1` => `1`, `"1"` => `"1"`)
- 오토핫키에서 지원하지 않는 타입인 `true`, `false`, `null` 을 각각 `json_true()`, `json_false()`, `json_null()` 함수로 대응
- Trailing comma 지원 (표준 json 지원안함)
- Single-line comments와 Multi-line comments 지원 (표준 json 지원안함)

## Contact
[카카오톡 오픈 프로필](https://open.kakao.com/me/neovis)
