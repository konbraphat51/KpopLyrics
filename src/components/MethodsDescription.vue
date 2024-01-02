<template>
	<div id="MethodsDescription">
		<details>
			<summary>Methods Description</summary>
			<p>
				<h3>TFIDF</h3>
				TFIDF indicates how important a word is to a document in a corpus.<br />
				<a
					href="https://medium.com/nlplanet/two-minutes-nlp-learn-tf-idf-with-easy-examples-7c15957b4cb3"
				>
					More information
				</a><br />

			</p>
			<p>
				<h3>LDA</h3>
				LDA is a topic modeling algorithm.<br />
				This automatically finds the topics in a set of documents.<br />
			</p>
			<p>
				<h3>NRC Emotion</h3>
				<a href="https://saifmohammad.com/WebPages/NRC-Emotion-Lexicon.htm">
					NRC Emotion is a lexicon for emotion analysis.
				</a> <br />
				Get the sum of emotion scores of each word in a document.<br />
				Then normalize the emotion vector norm to 1<br /> 
				Ratio against each population is rate of increase of population -> target.<br />
			</p>
			<p>
				<h3>Definitions</h3>
				<dl>
					<dt>Global population</dt>
					<dd>
						All musics in the global playlists such as billboard.<br />
					</dd>
					
					<dt>KPOP population</dt>
					<dd>
						Musics in the KPOP group.<br />
					</dd>

					<dt>Target population</dt>
					<dd>
						Musics in the target group.<br />
					</dd>

					<dt>Counting</dt>
					<dd>
						Count the times the word exceeded the threashold
					</dd>

					<dt>Sum</dt>
					<dd>
						Sum the score of the word
					</dd>
				</dl>
			</p>
		</details>
	</div>
</template>
