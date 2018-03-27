# coding:utf-8


import numpy as np
import matplotlib.pyplot as plt


def exam_du_2015_2_3(t, l):
    # t: distance between lines
    # l：length of needle
    if t <= l or t <= 0 or l <= 0:
        return 0

    k = 0.0
    n = 100000

    x = np.random.uniform(0, t / 2.0, n)
    y = np.random.uniform(0, t / 2.0, n)
    theta = np.random.uniform(0, np.pi, n)

    pos_neg = np.ones(theta.shape)
    pos_neg[theta >= np.pi / 2] = -1
    phi = theta + np.pi / 2 * pos_neg

    for i in range(n):
        if x[i] <= l / 2.0 * np.sin(theta[i]) or y[i] <= l / 2.0 * np.sin(phi[i]):
            k += 1

    return 1.0 - k / n


if __name__ == '__main__':
    t_input = 1
    l_input = 0.8

    timesOfRound = 100
    prob_mc = []
    for i in range(timesOfRound):
        prob_mc.append(exam_du_2015_2_3(t_input, l_input))

    prob_cal = 1.0 - (4.0 * l_input / (np.pi * t_input) - l_input ** 2 / (np.pi * t_input ** 2))

    err = np.array(prob_mc) - prob_cal
    avg = abs(err).mean()
    print('prob_mc - prob_cal={}'.format(err))
    print('mean absolute error is:{}'.format(avg))

    plt.figure()
    index = np.array(range(timesOfRound))
    plt.plot(index, err)
    plt.title('error')
    plt.xlabel('timesOfRound')
    plt.grid(True)
    plt.show()
