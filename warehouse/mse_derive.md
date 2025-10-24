## 1. MSE 정의

단순 선형 회귀에서 MSE(Mean Squared Error)는 다음과 같이 정의됩니다:
$$\text{MSE} = \frac{1}{n} \sum_{i=1}^n \left( y_i - (a x_i + b) \right)^2$$
여기서:
* $y_i$: 실제 값
* $a x_i + b$: 예측 값
* $n$: 데이터의 개수

MSE를 최소화하기 위해 $a$와 $b$에 대해 편미분하여 각각 0으로 설정합니다.

---

## 2. MSE를 $a$에 대해 편미분

먼저 MSE를 $a$에 대해 편미분합니다:
$$\frac{\partial}{\partial a} \text{MSE} = \frac{\partial}{\partial a} \left( \frac{1}{n} \sum_{i=1}^n \left( y_i - (a x_i + b) \right)^2 \right)$$
상수 $1/n$은 밖으로 빼낼 수 있으므로:
$$\frac{\partial}{\partial a} \text{MSE} = \frac{1}{n} \sum_{i=1}^n \frac{\partial}{\partial a} \left( y_i - (a x_i + b) \right)^2$$
제곱항을 미분하면 다음과 같습니다 (연쇄 법칙 적용):
$$\frac{\partial}{\partial a} \left( y_i - (a x_i + b) \right)^2 = 2 \left( y_i - (a x_i + b) \right) \cdot \frac{\partial}{\partial a} \left( y_i - (a x_i + b) \right)$$
여기서 $\frac{\partial}{\partial a}(y_i - (a x_i + b)) = -x_i$이므로:
$$\frac{\partial}{\partial a} \left( y_i - (a x_i + b) \right)^2 = -2 \left( y_i - (a x_i + b) \right) x_i$$
이를 전체 식에 대입하면:
$$\frac{\partial}{\partial a} \text{MSE} = \frac{1}{n} \sum_{i=1}^n \left[ -2 \left( y_i - (a x_i + b) \right) x_i \right]$$
상수 $-2$를 빼내면:
$$\frac{\partial}{\partial a} \text{MSE} = -\frac{2}{n} \sum_{i=1}^n x_i \left( y_i - (a x_i + b) \right)$$
이를 $0$으로 설정하여 최소화를 찾습니다:
$$-\frac{2}{n} \sum_{i=1}^n x_i \left( y_i - (a x_i + b) \right) = 0$$
양변에 $-n/2$을 곱하면:
$$\sum_{i=1}^n x_i \left( y_i - (a x_i + b) \right) = 0$$
괄호를 전개하면:
$$\sum_{i=1}^n x_i y_i - \sum_{i=1}^n a x_i^2 - \sum_{i=1}^n b x_i = 0$$
이를 $a$와 $b$에 관한 식으로 정리하면:
$$a \sum_{i=1}^n x_i^2 + b \sum_{i=1}^n x_i = \sum_{i=1}^n x_i y_i$$
(1)

---

## 3. MSE를 $b$에 대해 편미분

이번에는 MSE를 $b$에 대해 편미분합니다:
$$\frac{\partial}{\partial b} \text{MSE} = \frac{\partial}{\partial b} \left( \frac{1}{n} \sum_{i=1}^n \left( y_i - (a x_i + b) \right)^2 \right)$$
상수 $1/n$은 밖으로 빼낼 수 있으므로:
$$\frac{\partial}{\partial b} \text{MSE} = \frac{1}{n} \sum_{i=1}^n \frac{\partial}{\partial b} \left( y_i - (a x_i + b) \right)^2$$
제곱항을 미분하면 (연쇄 법칙 적용):
$$\frac{\partial}{\partial b} \left( y_i - (a x_i + b) \right)^2 = 2 \left( y_i - (a x_i + b) \right) \cdot \frac{\partial}{\partial b} \left( y_i - (a x_i + b) \right)$$
여기서 $\frac{\partial}{\partial b}(y_i - (a x_i + b)) = -1$이므로:
$$\frac{\partial}{\partial b} \left( y_i - (a x_i + b) \right)^2 = -2 \left( y_i - (a x_i + b) \right)$$
이를 전체 식에 대입하면:
$$\frac{\partial}{\partial b} \text{MSE} = \frac{1}{n} \sum_{i=1}^n \left[ -2 \left( y_i - (a x_i + b) \right) \right]$$
상수 $-2$를 빼내면:
$$\frac{\partial}{\partial b} \text{MSE} = -\frac{2}{n} \sum_{i=1}^n \left( y_i - (a x_i + b) \right)$$
이를 $0$으로 설정하여 최소화를 찾습니다:
$$-\frac{2}{n} \sum_{i=1}^n \left( y_i - (a x_i + b) \right) = 0$$
양변에 $-n/2$을 곱하면:
$$\sum_{i=1}^n \left( y_i - (a x_i + b) \right) = 0$$
괄호를 전개하면:
$$\sum_{i=1}^n y_i - a \sum_{i=1}^n x_i - b \sum_{i=1}^n 1 = 0$$
여기서 $\sum_{i=1}^n 1 = n$이므로:
$$a \sum_{i=1}^n x_i + b n = \sum_{i=1}^n y_i$$
(2)

---

## 4. 연립 방정식 정리

위에서 얻은 두 식 (1)과 (2)를 연립하여 $a$와 $b$를 구합니다:

$$a \sum_{i=1}^n x_i^2 + b \sum_{i=1}^n x_i = \sum_{i=1}^n x_i y_i \quad \text{(1)}$$
$$a \sum_{i=1}^n x_i + b n = \sum_{i=1}^n y_i \quad \text{(2)}$$

이 두 식을 풀면 (보통 식 (2)를 $b$에 대해 정리하여 식 (1)에 대입) $a$와 $b$의 값을 다음과 같이 얻습니다:

(이때 $\sum$는 모두 $\sum_{i=1}^n$을 의미합니다)

$$a = \frac{n \sum x_i y_i - \sum x_i \sum y_i}{n \sum x_i^2 - (\sum x_i)^2}$$
$$b = \frac{\sum y_i - a \sum x_i}{n}$$
