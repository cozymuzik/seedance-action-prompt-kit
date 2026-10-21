# Seedance Action Prompt Kit

Prompt templates and rules for making **continuity-locked action shots** with Seedance 2.0 / 2.5 (via Magnific, BytePlus ModelArk, Vigloo Studio), distilled from producing the AI SF-noir action series **CONSUMED (잠식)** solo.

Everything here came out of a failed take first. Rules are written as *symptom → why → how to write it instead*, so you can look up the failure you are seeing right now.

- Series: [Cozy Muzik on YouTube](https://www.youtube.com/@CozyMuzik)
- Maintainer: one person (the series' writer, director and producer). Early-stage and small.

## Who this is for

Solo AI filmmakers and short-form creators fighting the same things:

- identity drift (face, suit, build change between cuts)
- frozen poses (the start frame just sits there)
- cloned extras (3 guards become 5)
- reference images leaking into the video as its first or last frame
- action that reads as "two people standing and swinging"

## Files

| File | What it is |
|---|---|
| [TEMPLATE.md](TEMPLATE.md) | The 7 blocks every cut gets, the tag-block format, and the action-prose skeleton |
| [FAILURE_RULES.md](FAILURE_RULES.md) | Rules learned from failed takes — symptom → why → how to write it |
| [FIGHT_RULES.md](FIGHT_RULES.md) | Hard bans and a beat-writing method for hand-to-hand / VFX combat, plus a pre-run checklist |
| [EXAMPLE.md](EXAMPLE.md) | One complete 8-second action cut using every block |
| [PIPELINE.md](PIPELINE.md) | Which tool does which job, cost notes, and the per-cut workflow |

## How to use

1. Copy the 7 fixed blocks from `TEMPLATE.md` to the top of your prompt.
2. Write only the cut-specific part: camera, beats, body, sound list.
3. If it is a fight, run the `FIGHT_RULES.md` checklist before you spend credits.
4. When a take fails, find the symptom in `FAILURE_RULES.md` and change the wording, not the whole prompt.

## Scope

- Tested on Seedance 2.0 / 2.5 only, mostly 720p, 5–10 s cuts, Korean dialogue.
- Rules come from one production. Some will not transfer to your style. Treat them as a starting checklist.
- No paid prompt packs are reproduced here. Structures are described in my own words.

## Contributing

Open an issue with your own *symptom → fix* pair, including the model/provider and the wording that worked. Short entries are better than long ones.

## License

MIT.

---

## 한국어 요약

씨댄스 2.0/2.5로 액션 컷을 만들 때 캐릭터·동작·연출이 컷마다 흔들리지 않게 잡아주는 프롬프트 템플릿과 규칙 모음입니다. AI SF 느와르 액션 시리즈 **《잠식》(CONSUMED)**을 혼자 만들면서 실패한 테이크에서 뽑은 것만 적었습니다.

- `TEMPLATE.md` — 매 컷 들어가는 고정 7블록, 태그 블록 형식, 액션 프로즈 골격
- `FAILURE_RULES.md` — 실패 증상 → 원인 → 이렇게 써라
- `FIGHT_RULES.md` — 격투 컷 금지 목록, 비트 작성법, 돌리기 전 체크리스트
- `EXAMPLE.md` — 모든 블록을 쓴 8초 액션 컷 예시 한 개
- `PIPELINE.md` — 툴별 역할 분담, 비용 메모, 컷 하나 만드는 순서

규모는 작고 관리자는 한 명입니다. 본인 실패 사례(증상 → 고친 문장)를 이슈로 남겨 주시면 반영합니다.
