---
title: "Grid 布局算法"
date: 2018-04-29 16:10:53 +0800
categories: wpf uwp algorithm
published: false
---

---

* 测量过程
    1. 寻找所有行列范围中包含 Auto 和 * 的元素，使用全部可用尺寸提前测量
    1. 排除所有固定尺寸的行列，然后从总长中将其减掉
    1. 进行循环（以排除全部 min 要求的，*总长为负也要继续*）
        - 计算单位星长（单位星长 = 剩余总长 / 星数，最小为 0）
        - 找出第一个不满足 min 要求的 *，置其长度为 min，排除此行列，然后从总长中将其减掉
        - 所有的 * 检查完毕后，退出循环
    1. 进行循环（以排除全部 Auto，*总长为负也要继续*）
        - 计算单位星长（单位星长 = 剩余总长 / 星数，最小为 0）
        - 找到第一个 Auto，找到对此 Auto 的约束（跨行列或不跨行列都需要）
        - 对每个约束，检查目前尺寸是否满足约束（跨行列尺寸 >= Max(DesiredSize, min.Sum()）
        - 满足约束的忽略，不满足的约束需要计算约束大出行列的尺寸值，将此值设定为此 Auto 的待选长度
        - 当所有的约束检查完毕，在所有的待选长度中取最大值，设定为 Auto 的尺寸，排除此行列，然后从总长中将其减掉
        - 所有的 Auto 检查完毕后，退出循环
    1. 确定 Grid 的 DesiredSize
        - 如果剩余总长 >= 0，则 Grid.DesiredSize = 可用长度 - 剩余总长
        - 如果剩余总长 < 0，则返回的 Grid.DesiredSize = 可用长度，实际需求的 Grid.DesiredSize = 可用长度 - 剩余总长
    1. 如果总长 >= 0，则进行循环（以确定剩余全部子元素的测量所用尺寸）；否则直接将剩余 * 全部设置为 0
        + 进行循环
            - 计算单位星长（单位星长 = 剩余总长 / 星数）
            - 找出第一个不满足 max 要求的 *，置其长度为 max，排除此行列，然后从总长中将其减掉
            - 所有的 * 检查完毕后，退出循环
        + 至此，剩余的所有 * 都将不再有约束（即便元素 DesiredSize 不满足也无需处理，直接将元素裁剪）
            - 计算单位星长（单位星长 = 剩余总长 / 星数）
            - 计算所有剩余 * 的长度
        - 至此，所有子元素测量所用尺寸已经全部确定，使用此尺寸对子元素进行测量
    1. 分开保存 1~5、6 计算后的所得结果，布局过程即结束
* 排列过程
    1. 如果排列可用尺寸大于测量可用尺寸，则测量过程中的全部计算部分需要重新进行（因为可能此前的 min 现在不满足条件）
    1. 如果排列可用尺寸等于测量可用尺寸，则直接使用测量第 6 步的结果，依次进行排列，不足部分的空间全部使用 0
    1. 如果排列可用尺寸小于测量可用尺寸，则重新执行测量第 6 步的计算，以确定新的行列尺寸，依次进行排列，不足部分的空间全部使用 0