# FAILURE RULES — symptom → why → how to write it

Every entry here cost at least one take. Find your symptom, change that wording, run again. Don't rewrite the whole prompt.

전부 실패한 테이크에서 나온 규칙입니다. 증상을 찾아 그 문장만 고치세요.

Tested on Seedance 2.0 / 2.5 via Magnific, BytePlus ModelArk and Vigloo Studio. Frame counts assume 24 fps.

---

## A. Impacts and physics

### A1. A beam or laser "rises" slowly instead of hitting
**Why** Words like *rises / climbing / builds up* make the model animate the beam's growth.
**Write** "The beam appears fully formed in one frame. It does not travel." For sound, no "whine as it climbs".
빔은 "한 프레임에 이미 있다, 이동하지 않는다"로.

### A2. Camera is locked, impact happens, and nothing changes on screen
**Why** A locked camera plus "he is hit" gives the model nothing to show.
**Write** The impact as beats: 1-frame white flash → 2–3-frame camera shake → 3-frame hit-stop → consequence. During any hold before it, give micro-motion (shoulders drop, chest rises twice) so the body is not frozen.
피격은 플래시+카메라 흔들림+히트스톱 비트로. 기다리는 구간엔 호흡 동작을 준다.

### A3. Hit reaction is just a torso twist; the body stays where it was
**Why** "torso wrenches" is read literally.
**Write** Whole-body displacement: half a body-width back or sideways, a drop in height, limbs or wings flare. Add `FAIL if the body stays in place or only the torso turns`.
몸 전체가 밀려나야 한다. 상체만 돌면 실패 선언.

### A4. Frontal shot, "beam from the bottom of frame to the shoulder" → chest hit
**Why** A vertical line from bottom to shoulder passes through the chest; the model hits the chest.
**Write** Entry from a corner, diagonal, passing outside the torso, striking the outer edge of the screen-left shoulder. `FAIL if the chest is touched`.
정면 샷의 어깨 피격은 대각선 진입, 몸통 바깥 경유로. 가슴 맞으면 실패.

### A5. "Lower the stance / plant the feet" → the character sits down
**Why** Over-read.
**Write** Stance in numbers: "knees bent about 20°, hips stay above knee height, never sits or kneels".
자세 낮추기는 숫자로. "앉지 않는다" 명시.

### A6. Opponent bounces off the shield by himself
**Why** You described the shield, not the action.
**Write** The lead sends him flying; the shield only shows its geometry at the moment of contact.
방어막에 스스로 튕겨나가는 건 틀림. 주인공이 쳐서 날려야.

---

## B. References and composition

### B1. A reference image appears as the first or last frame
**Why** Default behavior: references get pasted in as frames.
**Write** `REFERENCES ARE NOT FRAMES: none of the reference images may appear as a frame anywhere in the video.` Every time.
"레퍼런스는 프레임이 아니다" 블록을 매번.

### B2. Angle changes between cuts (front → back) and the previous frame can't be inherited
**Why** A start frame from a different angle cannot continue.
**Write** Assign that image `DESIGN ONLY` (suit, colors) instead of `START FRAME`. Back views do not need a face lock at all.
앵글이 바뀌면 시작 프레임이 아니라 DESIGN ONLY로. 뒷모습은 얼굴 락 불필요.

### B3. A background or prop reference drags its camera angle into the shot
**Why** A picture taken from outside the room pulls the camera outside the room.
**Write** Tag it `TEXTURE ONLY` or `WEAPON DESIGN ONLY`, add "do not copy the camera angle", and put the camera-position block **first** in the prompt. Prefer a clean side-view of the object on black over a dramatic close-up.
배경·소품 레퍼런스는 역할을 질감·디자인으로 한정하고 카메라 위치 블록을 맨 앞에.

### B4. Chaining last frame → next start frame looks stiff
**Why** Same angle, same pose, no cut energy.
**Write** Make a fresh still from a new angle for the next cut and hard-cut in the edit. Chain frames only when the angle truly continues.
앞 컷 마지막 프레임을 다음 시작 프레임으로 잇지 않는다. 앵글을 바꾼 새 스틸로.

### B5. The start frame's color tone stays for the whole clip
**Why** Seedance keeps the start frame's lighting.
**Write** Fix the tone in the still first (e.g. switch blue standby light to red alert light with an image model), then generate.
톤은 영상이 아니라 시작 스틸에서 먼저 바꾼다.

### B6. The cut ends on a stiff frontal standing pose, or returns to the first composition
**Why** The model "settles" by default.
**Write** End mid-motion or on a natural turn/step, and describe the end frame. `FAIL if the last frame returns to the first composition`.
끝은 움직임 중이거나 자연스러운 전환. 첫 구도로 돌아가면 실패.

### B7. A designed key-art used as the *arrival* frame makes the ending look like an emblem
**Why** Arrival frames are rendered exactly; symmetric art reads as a logo.
**Write** Use the key-art as `DESIGN ONLY` and describe the arrival in text. Use start + arrival frames only for simple camera moves.
도착 프레임 방식은 단순 카메라 무브에만. 키아트는 DESIGN ONLY로.

---

## C. People, creatures, headcount

### C1. "Three guards" comes out as two, or four
**Why** Counts are soft.
**Write** Totals and positions: "LEAD 1 + GUARDS 3 = 4 people total. Two at the left wall, one at the right wall."
인원수는 합계와 각자 시작 위치까지.

### C2. Extras walking in from off-screen get cloned
**Why** Entering bodies get duplicated.
**Write** Everyone is on screen from frame 1. Only one person moves per cut; the others hold a pose (aiming, standing guard).
다인 컷은 전원 첫 프레임부터 배치, 움직이는 사람은 한 명.

### C3. Multi-person cuts built from text or character calls alone collapse
**Why** No composition to hold on to; small figures lose identity.
**Write** Make a still with everyone placed (any image model) and use it as `START FRAME`; use character calls for voice and identity only. Keep people above about one-fifth of frame height — waist-up medium two-shot, not a wide.
두 명 이상이면 전원 배치된 스틸을 시작 프레임으로. 인물이 화면 1/5보다 작아지면 락이 풀린다.

### C4. Two faces in one cut blend into each other
**Why** Face references mix.
**Write** One face per cut. Give the second person a cut of their own, or show them from behind.
얼굴은 한 컷에 한 명.

### C5. Three of the same thing come out identical (three guards, three water-snakes)
**Why** Copy-paste is the default.
**Write** Same shape and size, **different motion**: pose, height, phase of the movement. Don't vary thickness or scale — then they read as different objects.
같은 게 여럿이면 모양·크기는 같게, 모션만 다르게.

### C6. "Drone wreckage" comes out as crashed cars
**Why** "Wreckage" defaults to vehicles.
**Write** Describe the object: "matte-black quadcopter, four rotor arms, single red eye, about 1 m across". `FAIL if cars, trucks or planes appear`.
잔해는 생김새를 명시. 차 나오면 실패 선언.

### C7. Left/right instructions get flipped; a missing limb grows back
**Why** Seedance mirrors freely; body modifications don't survive text.
**Write** Anchor sides to a reference ("same side as the stump in @Image1") and attach a `BODY LOCK` image where the feature is clearly visible.
좌우는 레퍼런스 기준으로 묶고, 신체 변형은 BODY LOCK 이미지로.

### C8. Armed extras shown empty-handed make the scene read wrong
**Why** Guards standing around with nothing in hand look like they are holding the boss captive.
**Write** Give extras their props and a pose from frame 1.
경비는 총 들고 서 있어야 한다. 빈손이면 사로잡힌 그림이 된다.

---

## D. Text, dialogue, audio

### D1. On-screen text written in English renders as Chinese-looking glyphs
**Write** `NO TEXT` on any screen; use noise, static, graphs instead.
화면 글자는 금지. 노이즈·그래프로 대체.

### D2. Korean dialogue in an English prompt comes out in the wrong language
**Write** State "dialogue in Korean" and write the line in Hangul inside `[Sound]`.
한국어 대사는 "한국어"라고 쓰고 한글 원문 그대로.

### D3. Lip-sync fails when the prompt says "silent until 3 s" but the audio starts at 0 s
**Why** The file wins.
**Write** Pad the silence into the audio file itself, then state "the file has N s of silence, then the line". Keep dialogue cuts as short as the audio plus a little.
무음은 파일에 붙이고, 프롬프트에 "N초 무음 후 대사"라고 적는다.

### D4. The model invents a new voice for a line you didn't give audio for
**Write** Only lines that have a voice file or a registered voice. On Magnific the audio node is a *tone reference*: the words in `[Sound]` are what gets spoken, in that tone. One voice per character, forever.
캐릭터 목소리는 하나. 매그니픽에선 오디오 파일이 톤 참고, 대사는 [Sound] 텍스트.

### D5. ModelArk refuses the whole job: "generated audio may be subject to copyright"
**Write** Audio OFF, run again, add sound in the edit.
오디오 끄고 재시도.

### D6. Magnific Seedance takes only one audio slot
**Write** Put the speaker who is on screen in the slot; layer the second voice (radio, off-screen) in the edit.
오디오 한 개만 들어간다. 두 번째 목소리는 편집에서.

---

## E. VFX wording

### E1. "A straight line of fire" becomes a laser beam
**Write** "a rough braid of fire and steam", never "straight line".
"곧은 불의 선"이라 쓰면 레이저가 된다.

### E2. "Cooling into dark smoke / like rocket exhaust" turns a fire trail gray
**Write** "ribbons of red fire, thin white steam, no gray or black smoke; it ends as red embers".
연기 단어를 쓰면 불이 회색 연기로 변한다.

### E3. "A hole in the clouds with ripple rings" becomes a vortex or portal
**Write** Don't describe cloud openings as rings. Leave the clouds alone and give that moment its own cut.
구름 구멍+고리 → 소용돌이로 나온다.

### E4. "Layered individual feathers" in an image editor gives real bird plumage
**Write** For image edits: "wings made of fire, no white/cream/beige plumage". Video prompts can keep the feather wording; image prompts can't.
이미지 편집에선 "불로 된 날개"로. 영상 문구와 다르다.

### E5. Floating holograms or markers over a hand look pasted on
**Write** Keep VFX attached to the body or weapon. No floating UI, triangles, targeting marks.
떠 있는 그래픽은 쓰지 않는다. 이펙트는 몸·무기에 붙어 있어야.

### E6. A creature that must *form, fold and launch* in one 10 s fails on the launch
**Why** Two transformations in one clip; the second collapses into a blob.
**Write** Split birth and launch into separate cuts. One transformation per clip.
변신은 한 클립에 하나. 탄생과 발사는 컷을 나눈다.

### E7. Wings sprouting from the back, or a whole separate bird appearing
**Write** The effect lives in the trail of the blade or limb only, and only while it moves.
등에서 날개 돋기·별도 새 형체 금지. 잔상은 궤적에만.

---

## F. Providers, filters, limits

### F1. Face references rejected as "real person" even though the face is AI
**Why** Image-only filter; prompt text saying "AI character" does nothing.
**Write** Route face cuts to a provider that accepts face references; send faceless angles elsewhere. Don't rewrite the prompt — it isn't read by the filter.
얼굴 필터는 이미지만 본다. 얼굴 컷은 받아주는 툴로.

### F2. Human face start frame + "bound, struggling" + monster transformation → repeated content blocks
**Write** Split: a human cut (about 4 s, no monster reference) and a monster cut starting from a monster still of the same composition.
사람 컷과 괴물 컷으로 나누면 통과.

### F3. "Prompt is too long"
Magnific Seedance limit is 10,000 characters (10,844 was rejected).
프롬프트 1만 자 제한.

### F4. Draft/preview mode looks cheap but isn't
480p draft (~$1) only upgrades to 1080p (~$5.7 per 10 s). If you deliver 720p, running 720p once is cheaper.
드래프트 모드는 720p 한 번보다 비싸다.

### F5. Same prompt, different provider, different result
Vigloo exposes a "camera fixed" toggle; Magnific doesn't (write "Locked-off camera"). Vigloo characters carry a registered voice; Magnific needs a tone file. Keep a one-line provider note in your settings bullets.
툴마다 토글이 다르다. 설정 메모에 적어 둔다.
