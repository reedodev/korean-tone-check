<p align="center"><img src="docs/banner.png" alt="한국어 말투 점검: 존댓말 글에 섞인 반말 한 줄을 찾아냅니다" width="100%"></p>

<p align="center">
<a href="https://github.com/reedodev/korean-tone-check/actions/workflows/test.yml"><img src="https://github.com/reedodev/korean-tone-check/actions/workflows/test.yml/badge.svg" alt="test"></a>
<img src="https://img.shields.io/badge/Claude_Code-skill-2547F4" alt="Claude Code skill">
<img src="https://img.shields.io/badge/license-MIT-black" alt="MIT">
</p>

# 한국어 말투 점검 (korean-tone-check)

글에 섞인 합니다체·해요체·반말 종결을 찾아 목표 말투와 다르면 실패로 멈추고, AI 티가 나는 상투어·번역투·짧은 문장 나열은 참고로 표시합니다. 블로그, SNS, 카드뉴스, 영상 대본을 발행하기 직전에 씁니다.

<!-- prereq-adapt -->
## 무엇이 필요한가요?

꼭 필요한 것은 Node 18 이상, 검사할 글 파일(.md 또는 .txt), 목표 말투 한 가지입니다. 권장·선택 준비물까지 정리한 표는 [SKILL.md의 준비물](skills/korean-tone-check/SKILL.md#준비물-쓰기-전에-있어야-하는-것)에 있습니다.

## 바꿔 쓰기

에이전트에게 다음처럼 말하면 옵션을 바꿔서 실행합니다.

- "이 글은 해요체로 맞춰 줘" → `--target haeyo` (합니다체는 `hamnida`, 칼럼·기사체는 `plain`)
- "'게임 체인저', '혁신적인' 같은 말은 내 글에서 빼 줘" → `--cliches my-list.txt` 한 줄에 하나씩 `표현|이유`로 적습니다
- "짧은 문장 지적이 너무 많아" → `--min-run 5` (몇 문장이 이어질 때 지적할지), `--short 10` (짧다고 볼 글자 수)

말과 옵션의 대응표는 [SKILL.md의 바꿔 쓰기](skills/korean-tone-check/SKILL.md#바꿔-쓰기-이렇게-말하세요)에 있습니다.

## 설치

**Claude Code 플러그인으로 설치**

```
/plugin marketplace add reedodev/korean-tone-check
/plugin install korean-tone-check@korean-tone-check
```

**폴더만 복사**

```bash
git clone https://github.com/reedodev/korean-tone-check.git
cp -r korean-tone-check/skills/korean-tone-check ~/.claude/skills/
```

필요한 것: Node 18+

## 바로 해 보기

```bash
node skills/korean-tone-check/scripts/check-tone.mjs skills/korean-tone-check/examples/sample.md --target hamnida
```

자세한 절차, 옵션, 한계는 [SKILL.md](skills/korean-tone-check/SKILL.md)에 있습니다. 에이전트가 이 파일을 읽고 그대로 따릅니다.

## 시험

`node tests/run.mjs`가 SKILL.md 형식을 검사하고 예시 파일로 스크립트를 실제로 실행합니다. 푸시할 때마다 GitHub Actions가 같은 시험을 돌립니다(위 test 배지).

## 만든 사람

**리도**, AI 좌충우돌 실습 중인 20년차 엔지니어입니다. 매일 AI에게 일을 맡기다가 막힌 부분을 고쳐 가며 이 스킬을 만들었습니다.
[YouTube @Reedodev](https://www.youtube.com/@Reedodev) · [Threads @reedo.dev](https://www.threads.com/@reedo.dev) · [GitHub @reedodev](https://github.com/reedodev)

같이 만든 다른 스킬: [옵시디언 3D 지식그래프](https://github.com/reedodev/obsidian-brain-3d) · [노트 먼저 찾아보기](https://github.com/reedodev/vault-recall) · [작업 기록 강의자료](https://github.com/reedodev/work-to-lecture-deck) · [네이버 황금키워드](https://github.com/reedodev/naver-golden-keywords) · [한글 양식 채우기](https://github.com/reedodev/hwpx-form-fill) · [TTS 끝소리 고치기](https://github.com/reedodev/tts-tail-fix) · [카드뉴스 렌더](https://github.com/reedodev/html-card-render) · [영상 비율 검사](https://github.com/reedodev/social-video-gate) · [유튜브 게시 점검](https://github.com/reedodev/youtube-publish-checklist)

---

## English

Flags mixed Korean speech levels (formal/polite/plain), stock AI phrases, translationese and choppy sentence runs. Exits 1 on speech-level mismatches so an agent cannot publish a mixed draft.

Install: `/plugin marketplace add reedodev/korean-tone-check` then `/plugin install korean-tone-check@korean-tone-check`, or copy `skills/korean-tone-check` into `~/.claude/skills/`. See [SKILL.md](skills/korean-tone-check/SKILL.md) for the full procedure. MIT License; third-party models, fonts and libraries keep their own licenses.
