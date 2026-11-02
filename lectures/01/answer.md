# 第1回 解答

## 演習

- 講座に固有の質問（宿題の3レベル）へのモデルの回答（要約でよい）：講座固有の質問では、講座の情報を知らないため、分からないと答えるか、一般的な意味から推測した回答になった。
- 用語集の正しい意味と比べて気づいたこと：用語集では、宿題の3レベルは基礎・実装・発展の3段階である。素のLLMはこの講座固有の定義を知らないため、もっともらしい回答でも正しいとは限らない。
- 表示できたトークン数（入力 / 出力）：`[usage] input_tokens=7 output_tokens=...` の形式で表示できた。今回の実行では、入力はすべて `7` トークンで、出力は回答によって `576`〜`667` トークンだった。

## 宿題

- 取り組んだレベル：基礎
- やったこと：同じ質問「LoRAとは何ですか？」を、`gemini-3.5-flash` と `gemini-3.5-flash-lite` のモデルで実行し、回答とトークン数を比較した。
- 結果：実際の出力は次のようになった。

	```text
	AIE_MODEL=gemini-3.5-flash uv run python -m app.ask "LoRAとは何ですか？"
	[model] gemini-3.5-flash
	[質問] LoRAとは何ですか？

	[usage] input_tokens=7 output_tokens=594
	**LoRA（ローラ / Low-Rank Adaptation）**とは、大規模なAIモデルを効率的かつ低コストで追加学習させるための技術です。

	uv run python -m app.ask "LoRAとは何ですか？"
	[model] gemini-3.5-flash-lite
	[質問] LoRAとは何ですか？
	[usage] input_tokens=7 output_tokens=576
	**LoRA（ローラ）**とは、「Low-Rank Adaptation（低ランク適応）」の略で、AIのファインチューニングを効率よく行うための技術です。

	uv run python -m app.ask "LoRAとは何ですか？"
	[model] gemini-3.5-flash-lite
	[質問] LoRAとは何ですか？
	[usage] input_tokens=7 output_tokens=654
	**LoRA（ローラ）**とは、「Low-Rank Adaptation（低ランク適応）」の略で、AIのファインチューニングを効率よく行うための技術です。

	uv run python -m app.ask "LoRAとは何ですか？"
	[model] gemini-3.5-flash-lite
	[質問] LoRAとは何ですか？
	[usage] input_tokens=7 output_tokens=667
	**LoRA（ローラ）**とは、AIの分野で使われる技術で、「Low-Rank Adaptation（低ランク適応）」の略です。
	```

	出力トークン数を比較すると、`gemini-3.5-flash` は `594`、`gemini-3.5-flash-lite` は順に `576`、`654`、`667` だった。同じモデル・同じ質問でも、説明の詳しさや例えが毎回少しずつ変わった。どの回答も、LoRAはモデル全体を変更せず、一部の追加パラメータだけを学習する技術だと説明していた。
- 気づき・疑問：モデルを変えると出力トークン数や説明の詳しさが変わった。また、同じモデルに同じ質問をしても回答は完全には同じにならなかった。入力トークン数は同じ質問なので同じだったが、出力トークン数は回答の長さに応じて変化した。
