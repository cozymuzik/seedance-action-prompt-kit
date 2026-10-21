# PIPELINE — who does what

One person, one laptop, one series. This is the division of labor that survived.

혼자 만드는 파이프라인에서 살아남은 역할 분담입니다.

## Tools and their jobs

| Job | Tool | Notes |
|---|---|---|
| Key stills, start frames, asset sheets | GPT image model | Character sheet, VFX sheet, weapon side-view on black. One fix per round. |
| Face cuts, dialogue cuts | Magnific · Seedance 2.5 | Accepts face references. One audio slot. 10,000-character prompt limit. No camera-lock toggle → write "Locked-off camera". Start frame goes in the **image-start** slot, not the reference slot. |
| Unmanned / pure-VFX cuts | BytePlus ModelArk · Seedance 2.5 | Rejects references with visible faces (image-only filter; prompt text doesn't help). Audio ON can trigger a copyright refusal → OFF and retry. |
| Character-call cuts | Vigloo Studio · Seedance 2.5 | Registered characters with a built-in voice ("in his registered voice"), "camera fixed" toggle for locked shots. |
| Voices | ElevenLabs | One voice per character, forever. Never let the video model invent a voice. |
| Image fixes | Magnific image edit | Pose → weapon → wings: one change per round. A reference that contains the wrong shape beats any text. |
| Assembly, second voice, radio FX, color | CapCut | Layer the second speaker here when the video tool takes one audio. Cut around a bad second with a cutaway instead of regenerating. |

툴별 역할: 스틸은 GPT, 얼굴·대사 컷은 매그니픽, 무인 컷은 ModelArk, 캐릭터 호출 컷은 비글루, 목소리는 일레븐랩스, 이미지 수정은 매그니픽, 합치기는 캡컷.

## Cost rules

- Always 720p. No cut has needed 1080p for a short.
- 480p draft (~$1) only continues to 1080p (~$5.7 per 10 s) → more than one 720p run. Not used.
- Regenerate only when the error is in the first few seconds. Later errors: trim, cutaway, or cover with the next cut.
- Don't start a new prompt while a take is still rendering.

항상 720p. 드래프트 모드 안 씀. 뒤쪽 오류는 재생성 대신 편집.

## Per-cut workflow

1. **Settle the situation first.** What happened one beat before this cut, and how the cut is entered. No prompt until the beats are agreed. — 상황과 앞 컷 연결이 정리된 다음에 프롬프트.
2. **The video always moves.** A start pose that holds is a failed cut. — 시작 포즈가 그대로 멈춰 있으면 실패.
3. **Make the still.** New angle, everyone placed, color tone already correct. — 스틸부터, 앵글은 새로.
4. **Prompt** = 7 fixed blocks + cut-specific part (`TEMPLATE.md`). Fight? Run the `FIGHT_RULES.md` checklist. — 템플릿과 전투법칙.
5. **Run once at 720p.** Review at 1× and frame-by-frame around the impact. — 720p 한 번, 임팩트 구간은 프레임 단위로 확인.
6. **Fix one thing** per retry, by changing the wording that caused it (`FAILURE_RULES.md`). — 한 번에 하나만 고친다.
7. **Edit.** Trim, cutaway, layer audio, radio/alarm effects, color. — 편집으로 마무리.

## Continuity habits

- Never delete old threads or logs. When a canon color or shape drifts, check the earlier footage, not memory.
- Keep a character sheet and a VFX sheet; attach them to every cut that needs them.
- Save the last frame of a successful cut as a design reference, not as the next start frame.
- The start frame's lighting persists through the clip. Fix it in the still.
- Dialogue cuts: audio-file timing = prompt timing. Pad silence into the file.

옛 스레드와 로그는 안 지운다. 설정이 헷갈리면 기억 말고 이전 영상을 본다.
