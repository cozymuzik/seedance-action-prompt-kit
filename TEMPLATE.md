# TEMPLATE — the fixed part of every cut

Two layers: a **settings note** you keep above the prompt (for yourself), and the **prompt** itself, which always opens with the same 7 blocks and then the cut-specific part.

프롬프트는 두 층입니다. 위에 **설정 메모**(나를 위한 것), 그 아래 **프롬프트**(고정 7블록 + 컷마다 바뀌는 부분).

## 0. Settings note (above the prompt, not inside it)

Write this as bullets in your own language. It is not sent to the model.

- Tool / Seedance version (e.g. Magnific · Seedance 2.5)
- Aspect ratio · resolution · duration (e.g. 16:9 · 720p · 8s)
- Audio on/off (and the music toggle, if the tool has one)
- Character call, if the tool supports registered characters (e.g. `@Lead`)
- `@Image1`, `@Image2`, … — one line each: what the image is and what role it plays (see block 2)

설정은 프롬프트 안에 [Settings] 블록으로 넣지 않습니다. 모델이 읽을 필요가 없는 정보입니다.

## The seven fixed blocks

### 1. IDENTITY LOCK — always first
Who the lead is and what may never change: body type, suit/costume, helmet or hair, colors, and the sheet it must match.

Example: `IDENTITY LOCK: Lead = @Image1 (character sheet). Slim build, never bulky. Matte-black suit, no glow. Closed round helmet, large visor, no hair visible. Any deviation = wrong.`

맨 위. 캐릭터가 누구이고 절대 바뀌면 안 되는 것(체형·슈트·헬멧·색·기준 시트).

### 2. REFERENCE ROLES + "REFERENCES ARE NOT FRAMES"
One line per image, with one of these roles:

- `START FRAME` — the video's first frame must match this image.
- `DESIGN ONLY` — copy suit/colors/shape; ignore pose, angle, background.
- `TEXTURE ONLY` / `WEAPON DESIGN ONLY` — copy material or object design; **do not copy the camera angle**.
- `BODY LOCK` — a physical feature (e.g. a missing arm) that text cannot hold; tie left/right to it: "same side as in @Image1".

Then always:

`REFERENCES ARE NOT FRAMES: none of the reference images may appear as a frame anywhere in the video.`

Without this line Seedance tends to paste a reference image in as the first or last frame, and the viewer feels they are seeing the same picture twice.

@Image마다 역할을 적고 "레퍼런스는 프레임이 아니다"를 꼭 붙입니다. 안 붙이면 참고 이미지가 영상 처음이나 끝에 그대로 박힙니다.

### 3. PACING LOCK
Timestamps. What happens in each window, and when the big beat lands.

Example: `0.0–1.5s hold with breathing · 1.5–2.0s whip-pan · 2.0–2.3s impact (white flash 1 frame, hit-stop 3 frames) · 2.3–5.0s consequence · 5.0–8.0s settle into end frame`

몇 초에 뭘 할지 시점으로 박습니다. 안 박으면 모델이 처음 2초를 낭비합니다.

### 4. FAIL DECLARATIONS
Name the failure you are afraid of. The model reads these.

Example: `FAIL if: the body stays in place after the hit · only the torso twists · a car or truck appears in the debris · the camera moves in front of the lead · the last frame returns to the first composition.`

"~하면 틀린 것"을 명시합니다. 무서운 실패를 그대로 적으면 됩니다.

### 5. VFX CONTINUITY RULE
One line that fixes the persistent state of your signature effect: what stays on, what shape it keeps, what it never becomes.

Example: `Wings stay fully spread for the whole cut, individual feathers of fire; never fold, never become a bird.`

시그니처 이펙트의 "유지 상태"를 한 줄로 고정합니다(펼친 채 유지, 형태, 절대 안 되는 것).

### 6. SPEED LIVES IN BACKGROUND AND CAMERA
Do not ask the body to "move fast". Put speed into background streaking, whip-pans, motion blur, camera shake, and how fast things break.

속도는 몸이 아니라 배경과 카메라가 표현합니다.

### 7. NO MUSIC
`[No BGM]` plus a plain sound list (ambient, impacts, voice). Generated music fights your edit and triggers audio-copyright blocks on some providers.

음악 없음. 효과음·앰비언트 목록만.

## Cut-specific part (changes every cut)

- Camera: position first, then the move per beat (push-in, whip-pan, whip-tilt, dutch, orbit, low/high/ground).
- Beats: 2–3 big moves per 8 s, one physical consequence each.
- Body: posture, stance height, where the lead moves from → to.
- Sound list (and dialogue text with its language).

컷마다 바뀌는 것: 카메라, 비트, 몸 자세, 사운드 목록.

## Tag-block format

Works on Vigloo, Magnific and ModelArk alike.

```
[No BGM]
[ONLY ...]        one line: who/what is in frame, nothing else
[Reference]       @Image roles + REFERENCES ARE NOT FRAMES
[Character]       identity lock
[Others]          extras, creatures, headcount with totals and positions
[Global]          look line (see skeleton below)
[Cut]             beats with timestamps
[Camera]          position, moves, locked or tracking
[Look]            lens, grain, palette, light
[Sound]           sound list / dialogue text (and language)
```

## Action-prose skeleton (fight and impact cuts)

Used inside `[Cut]` when the cut is action. In this order:

1. **Global line** — photoreal live action, ARRI Alexa + anamorphic, film grain, practical rain/fire/water/spark particles.
2. **Body/camera contract** — stunt-realistic bodies, impossible camera choreography.
3. **Ambient sound list** — no music, no dialogue.
4. **Per-second prose** — each beat: one big action + its physical result (spray, sparks, a body flying) + a camera move (Z-axis push, whip-pan, whip-tilt, dutch, orbit) + a 2–3 frame hit-stop on contact.
5. **End frame** — "settle into the end frame: …" and describe it. Never the first composition.
6. **Closing paragraph** — handheld energy, particle density, palette.

Rule of thumb: 8 s = 2–3 big moves. Camera-angle changes, action and speed changes (burst, hit-stop, ramp) happen together, not one at a time.

액션 컷 프로즈 순서: 글로벌 한 줄 → 신체·카메라 약속 → 사운드 → 초 단위 비트(동작+물리 결과+카메라+히트스톱) → 엔드프레임 → 마무리 문단. 8초에 큰 동작 2~3개.
