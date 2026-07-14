# 샤플리 분배 계산기

협조적 게임이론의 **샤플리 밸류(Shapley Value)**를 계산하고, 여기에 윤리적 가치를 도입할 때
정확히 **어떤 공리를 포기해야 하는지**를 보여주는 도구.

자율적 교육과정 탐구보고서 「샤플리 밸류와 글로벌 공급망의 분배」의 부속 프로그램.

## 구현 내용

**01 특성함수 v(S) 설정**
A(설계·브랜드) / B(핵심부품) / C(조립)의 3인 협조적 게임. 7개의 v(S) 값을
슬라이더와 숫자칸으로 조정. C가 더미 플레이어인지 실시간 판정.

**02 샤플리 밸류**
- 방법 1: 6가지 합류 순열을 전부 전개
- 방법 2: 공식 φᵢ(v) = Σ [ s!(n−s−1)!/n! ] · [ v(S∪{i}) − v(S) ] 직접 적용
- 두 방법의 결과가 항상 일치함을 확인할 수 있음

**03 시도 1 — 특성함수에 윤리적 비용 빼기 (실패 시연)**
v\*(S) = v(S) − λ·D(S). 노동자를 보호하려 도입한 페널티가 오히려 노동자의 몫을 빼앗는다.
**가법성 공리** 때문에 φ(v − λD) = φ(v) − λ·φ(D)이고, φ(D) = (0, 0, λ)이므로
페널티 전액이 C에게 청구된다.

**04 시도 2 — 배분 규칙 자체 바꾸기 (성공)**
균등해 샤플리 밸류 φᵢ^α = α·φᵢ(v) + (1−α)·v(N)/n.
α를 1에서 떼는 순간 **네 공리 중 더미 공리 하나만 깨진다.**
C에게 목표 비율을 보장하는 α를 역산하는 기능 포함.

## 실행

빌드 없음. `index.html` 하나만 열면 된다.

```
# 로컬
open index.html

# Vercel
GitHub에 push → Vercel에서 Import → Framework Preset: Other → Deploy
```

## 참고 문헌

- Shapley, L. S. (1953). "A Value for n-Person Games." *Contributions to the Theory of Games, Vol. II*. Princeton University Press.
- van den Brink, R., Funaki, Y., & Ju, Y. (2013). "Reconciling marginalism with egalitarianism." *Social Choice and Welfare*, 40(3).
- Kraemer, K. L., Linden, G., & Dedrick, J. (2011). *Capturing Value in Global Networks: Apple's iPad and iPhone*. UC Irvine.
