---
name: domn-director-emotion-review
description: |
  Review emotionally driven dramatic scenes for truthful micro-actions, playable objectives, dialogue rhythm, and cinematic continuity. Use for emotion-scene review, breakup scenes, romance performance notes, screenplay diagnosis, micro-expression checks, or generative-video prompt controllability checks. Accept screenplay, scene, storyboard, or video-prompt text; identify the source form before review and return a source-format revision for the matching branch.
---

# DOMN Director Emotion Review

Review an emotionally charged scene without confusing a screenplay with a generative-video prompt. The first task is always input classification. Preserve the user's source form in the final revision.

## Step 1: Classify The Input

Classify before interpreting the scene. Report the classification and the evidence in one short line.

### Screenplay

Classify as `SCREENPLAY` when the text is primarily a dramatic work for actors and production: scene headings, action paragraphs, character cues, dialogue, parentheticals, or screenplay-style transitions. A screenplay may contain camera language, but camera language alone does not make it a prompt.

### Generative-video prompt

Classify as `VIDEO_PROMPT` when the text is primarily an instruction to a video model: shot timecodes, aspect ratio, fps, lens, camera movement, image style, character locks, audio constraints, negative prompts, explicit generation parameters, or shot-by-shot prompt blocks with complete dialogue.

### Mixed or ambiguous input

If both forms are substantial, classify as `MIXED` and state which layer is dominant. Review the dominant layer first and list the other layer as a contamination risk. If the dominant layer cannot be determined, ask one concise clarification question before rewriting.

Never silently convert a screenplay into a video prompt or a prompt into screenplay prose.

Completion criterion: return one classification line with confidence and evidence, or one clarification question when the dominant form cannot be determined.

## Step 2: Establish The Emotional Spine

Extract, without inventing facts:

- each character's immediate objective: what they want the other person to do now;
- obstacle: what prevents that objective;
- tactic: the current way they pursue it;
- emotional direction: the change from the start to the end of the scene;
- relationship geometry: who approaches, who withdraws, who controls the distance;
- turn points: the exact line, action, or silence that changes the power balance.

Use the following working model as an analysis aid, not as a claim that one gesture equals one emotion:

`state -> trigger -> objective -> impulse -> visible action -> inhibition -> voice/breath consequence -> after-effect`

Prefer observable evidence over labels such as “devastated,” “heartbroken,” or “cinematic.”

## Step 3: Review Micro-actions

Audit six channels. For every important beat, identify at least one visible or audible action and its timing.

1. Eyes: focus, avoidance, delayed return, fixation, loss of focus.
2. Eyelids/brows: heavy lids, one slow blink, brow release, brief inner-brow lift.
3. Mouth/jaw: swallowed word, held breath, jaw tighten/release, lips part then close.
4. Breath/voice: interrupted onset, short inhale, long exhale, pitch stability, falling volume, broken final syllable.
5. Hands/posture: reach-and-stop, grip, release, shoulder line, weight shift, feet that do not follow the torso.
6. Space/rhythm: distance, refusal to step closer, half-beat delay, silence after a line, fixed axis.

Write actions as compact, filmable clauses:

`body part + verb + direction + intensity + beat/time + inhibition or recovery`

The most valuable actions often contain an incomplete impulse: reaches but stops, starts to speak but resets the breath, looks back but does not approach. Do not add a micro-action to every sentence; choose the actions that change the audience's reading of the relationship.

Use onset / apex / offset when timing matters: the action begins, reaches a small peak, then returns to a new neutral state. Preserve habitual movements as neutral unless the source gives a reason to read them as emotion.

Completion criterion: every major emotional beat has a stimulus, a playable objective, and at least one timed visible or audible reaction.

## Step 4A: Screenplay Review Output

When classified as `SCREENPLAY`, output in this order:

1. `输入识别`: classification, confidence, and evidence.
2. `情绪戏诊断`: objective, obstacle, tactics, emotional arc, turn points.
3. `真人感检查`: micro-actions, breath/voice, subtext, unfinished impulses, silence, and whether reactions follow stimuli rather than appear arbitrarily.
4. `节奏检查`: beat density, dialogue length, reaction time, escalation, and the final after-effect.
5. `问题清单`: prioritized findings using `P0/P1/P2`; cite the source line or exact phrase when possible.
6. `修订建议`: suggest playable changes in screenplay language. Keep action lines visual and concise; do not add camera-generation parameters unless the source already uses them.
7. `修订片段`: only rewrite the affected excerpt, preserving scene headings, character cues, dialogue ownership, and screenplay formatting.

Keep this branch in screenplay language. Camera-generation parameters are relevant only when the source already uses them; their absence is not a screenplay defect.

Completion criterion: the findings and revised excerpt preserve screenplay scene headings, character cues, dialogue ownership, and screenplay action-line form.

## Step 4B: Video-prompt Review Output

When classified as `VIDEO_PROMPT`, output in this order:

1. `输入识别`: classification, confidence, and evidence.
2. `结构完整性`: global style, character locks, 180-degree axis, shot timing, camera, blocking, performance, dialogue, sound, and negative constraints.
3. `对白绑定检查`: every spoken line must have an explicit speaker and remain in the shot where it is performed. Check turn-taking, line order, timing, and whether actions are attached before/during/after the correct line.
4. `微动作可执行性`: replace abstract emotion labels with a small number of action clauses while preserving the original narrative shot structure. Keep the original headings, time ranges, shot descriptions, and complete dialogue.
5. `连续性与风险`: face/wardrobe drift, axis crossing, camera conflicts, overfull dialogue, contradictory motion, unsupported audio requirements, and negative-prompt collisions.
6. `问题清单`: prioritized `P0/P1/P2` findings with exact source phrases.
7. `修订版提示词`: rewrite in the original prompt's structure. Keep sections such as basic setting, performance tone, character setting, global constraints, shot-by-shot description, sound design, negative constraints, and core theme whenever they exist. Keep all dialogue verbatim unless the user explicitly requests line editing. Embed micro-actions next to the line they affect; never move dialogue into a detached action table.

Use [references/perfect-emotion-video-prompt.md](references/perfect-emotion-video-prompt.md) as the canonical structural exemplar for this branch. Match its section order, narrative density, shot time ranges, speaker-bound dialogue, embedded performance details, sound-design block, negative constraints, and core-theme ending. Treat it as a format and quality reference; do not copy its characters, setting, dialogue, or style into unrelated inputs.

Return the final prompt in its source prose and section format. Use JSON, a shot spreadsheet, or a detached action list only when the user explicitly requests that format.

## Step 5: Review Rules

- One shot should have one dominant emotional turn and a manageable number of principal actions.
- A camera instruction, a subject action, and a line of dialogue must not contradict each other.
- Preserve speaker labels and exact dialogue order. If a line is ambiguous, flag it rather than assigning it silently.
- Prefer “small head shake once before the line” over “looks devastated.”
- Prefer “second repetition is quieter; final syllable unstable” over “voice is emotional.”
- State timing only when it changes performance or synchronization; avoid fake precision.
- Use negative constraints as recognizable outcomes: text, watermark, extra people, facial drift, wardrobe change, exaggerated sobbing, lip-sync mismatch.
- Keep 180-degree axis, fixed left/right positions, and character anchors visible across shots when continuity is requested.
- Separate evidence from inference. Mark creative recommendations as recommendations, not facts.
- Treat absent backstory, diagnosis, actor intentions, and technical capabilities as unknown; label any additions as recommendations.

Completion criterion: every P0/P1/P2 finding points to a source phrase or a clearly labeled inference, and the revision introduces no ungrounded facts.

## Compact Review Heuristic

For each emotional beat, ask:

`What did the other person do? What does this character want now? What does the body try first? What stops it? What changes in the voice? What remains after the line?`

If a beat cannot answer at least four of these questions from observable text, mark it as under-specified and recommend a minimal revision.
