# Area Chart using Recharts and Tailwind CSS

```tsx
import React from "react"
import {
  Area,
  AreaChart,
  CartesianGrid,
  Legend,
  ResponsiveContainer,
  Tooltip,
  XAxis,
  YAxis,
} from "recharts"

import { numberWithCommas } from "@/lib/helper"
import { cn } from "@/lib/utils"

const data = [
  {
    name: "Page A",
    uv: 4000,
    pv: 2400,
    amt: 2400,
  },
  {
    name: "Page B",
    uv: 3000,
    pv: 1398,
    amt: 2210,
  },
  {
    name: "Page C",
    uv: 2000,
    pv: 9800,
    amt: 2290,
  },
  {
    name: "Page D",
    uv: 2780,
    pv: 3908,
    amt: 2000,
  },
  {
    name: "Page E",
    uv: 1890,
    pv: 4800,
    amt: 2181,
  },
  {
    name: "Page F",
    uv: 2390,
    pv: 3800,
    amt: 2500,
  },
  {
    name: "Page G",
    uv: 3490,
    pv: 4300,
    amt: 2100,
  },
]

export default function AreaChartExample() {
  return (
    <ResponsiveContainer width="100%" height="100%">
      <AreaChart width={500} height={300} data={data}>
        <CartesianGrid strokeDasharray="3 3" opacity={0.3} vertical={false} />
        <XAxis
          dataKey="name"
          axisLine={false}
          tickLine={false}
          height={55}
          fontSize={14}
          textAnchor="end"
          stroke="#e5e5e5"
          interval={0}
        />

        <YAxis
          axisLine={false}
          tickLine={false}
          tick={{ dx: -7 }}
          stroke="#e5e5e5"
          fontSize={14}
        />

        <Tooltip
          wrapperStyle={{ outline: "none" }}
          cursor={{ fill: "#fafafa", opacity: "0.15" }}
          content={({ payload, label }) => {
            return (
              <div className="min-w-[8rem] divide-y divide-brand-200 rounded-md border border-brand-200 bg-brand-50 text-brand-700 shadow dark:divide-brand-700 dark:border-brand-700 dark:bg-brand-900 dark:text-brand-200">
                <p className="px-4 py-1.5">{label}</p>
                <div>
                  <ul className="px-4 py-1.5">
                    {payload.map((p, i) => {
                      return (
                        <li key={i} className="text-sm">
                          <svg
                            className={cn("mr-2 inline h-2 w-2")}
                            fill={i === 0 ? "#60a5fa" : "#fbbf24"}
                            viewBox="0 0 8 8"
                          >
                            <circle cx={4} cy={4} r={4} />
                          </svg>
                          {numberWithCommas(p.value.toString())}
                        </li>
                      )
                    })}
                  </ul>
                </div>
              </div>
            )
          }}
          position={{ y: 0 }}
        />
        <Legend
          layout="horizontal"
          verticalAlign="top"
          align="center"
          content={({ payload }) => {
            return (
              <ul className="flex w-fit gap-4 pb-6 pl-1">
                {payload.map((p, i) => (
                  <li key={i}>
                    <svg
                      className={cn("mr-2 inline h-2 w-2")}
                      fill={i === 0 ? "#60a5fa" : "#fbbf24"}
                      viewBox="0 0 8 8"
                    >
                      <circle cx={4} cy={4} r={4} />
                    </svg>
                    {p.value}
                  </li>
                ))}
              </ul>
            )
          }}
        />

        <defs>
          <linearGradient id="primary" x1="0" y1="0" x2="0" y2="1">
            <stop offset="5%" stopColor="#60a5fa" stopOpacity={0.4} />
            <stop offset="95%" stopColor="#60a5fa" stopOpacity={0} />
          </linearGradient>
        </defs>

        <defs>
          <linearGradient id="secondary" x1="0" y1="0" x2="0" y2="1">
            <stop stopColor="#fbbf24" stopOpacity={0.1} />
          </linearGradient>
        </defs>
        <Area
          dataKey="pv"
          strokeWidth={2}
          dot={false}
          activeDot={{
            stroke: "#171717",
          }}
          stroke="#60a5fa"
          fill="url(#primary)"
        />
        <Area
          dataKey="uv"
          strokeWidth={2}
          dot={false}
          activeDot={{
            stroke: "#171717",
          }}
          stroke="#fbbf24"
          fill="url(#secondary)"
        />
      </AreaChart>
    </ResponsiveContainer>
  )
}
```
