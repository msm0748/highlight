<script>
	let contentEl;
	const content = `
<h1>sdafasdfsadfsadf</h1><ul><li>안녕하세요</li><li>안녕하세요</li></ul><p>A mother’s firstconcern is about whether she can maintain the life and growth of her baby (Stern, 1995). Feeding the infant and seeing it develop is a primary task which all parents wish to fulfil. Most mothers want<br>only the best fortheir offspring. In turn, the child possesses an inborn drive to move forward,to grow and to progress − children are meant to thrive. Sadly, this fundamental right is missing for many infants all over the world. When things go wrong, when the growth of the baby is impeded for whatever reason, it becomes aserious and profoundproblem for the parents. It is worth reflecting on the meaning of naming this condition “failure tothrive”: does it not imply failure on the part of the caregiver? Could this not do aninjustice to the parent? In future wemay consider“faltering weight” as a better,less pejorativeterm todescribe this condition.<br>Feeding varies considerably among children during infancy and feeding problems are very common, affectingup to 30% of infantsdepending on how feeding problems are defined. However,disorders of feeding are often examinedonly in terms of functional or anatomic impairments. The causesof infantfeeding problems are multifactorial, not well known and overlapping the fields of paediatrics and mental health,although physical causes need to alwaysbe excluded.<br>Research has shown that in developing countrieschildren under the age of 5years areprevented from reaching their fullpotential because of exposure to multiple risk factors. Poverty plays acentral role in mental health in general for adults (Lund C et al, 2010), but particularly it does so for youngchildren. Malnutrition in the earlyyears has serious consequences for brain development (Grantham-McGregor et al, 2007) whichcould adverselyaffect children’s later ability to learn andprogress in school. The long term adverse effect of failure tothrive on cognitive ability should not be underestimated; it has been estimated to be around 4 IQ points. (Corbett &amp; Drewett, 2004)It is important for infantand childhealth workers to know thatmalnutrition is not simply a matterof inadequate food intake or physical illness,but that it can be a manifestation of things having gone wrong in the relationship betweenmother and child. The term feeding does imply that a two-way relationship ispart of eating in early childhood (Chatoor, 2002) − a delicate interplay existsbetween mother andchild inthe feedingsituation. While the World HealthOrganization recognizes the importance of response caregiving for young children, there is insufficient emphasison the centrality of the caregiver-child relationship in the actual feeding situation.This chapter focus specifically on how priority can be given to the relationship between caregiver andchild within the contextsof aprimary health care or home-based setting in adeveloping country such as South Africa. The categories which describe thevarious reasons for faltering weight are described. The focus throughout shallbe onthe very young child, under 12 months,bearing in mind that the effects of early problems in this domainextend far beyond the firstyear of life. The word “mother” isused to denote the adult whois themain caregiver and who fulfils the traditional “mothering” functions. It does not exclude other caregivers such as father,grandparents, day carers and foster parents.</p><h2>DEFINITIONS AND CLASSIFICATION</h2><p>Failure to thrive can be regarded as a descriptive umbrella for infants or toddlers who have difficulty in establishing regular feeding patterns and do not gain the expected weight.<br>Failure to thrivecan be regarded as a descriptive umbrella term which refers to inadequategrowth due to a nutritional deficiency. Failure to thrive is often used inclinical practice to mean that the current weight or rate of weight gain of achild are significantly below that expected of similar children of the same sexand age. There is no definite accepted measure to diagnose the condition; mostpractitioners diagnose failure to thrive when a child’s weight for age fallsbelow the fifth centile of the standard growth chart (see Appendix B.2.1).Although failure to thrive was once classified into organic and nonorganic, itis now seen to be the result of the interaction between the environment and thechild’s health, development and behaviour (Gahagan, 2006). Successful feedingis necessary not only for physical survival but is also tied in with theinfant’s general development.</p><p>안녀이하세요</p><p>ㅇㅇㄹㄴㅇㄹ</p>`;

	function findBlockIndex() {
		const selection = window.getSelection();
		if (selection.rangeCount > 0) {
			const range = selection.getRangeAt(0);

			const selectedText = selection.toString();
			if (selectedText.length > 0) {
				// 선택된 범위의 공통 조상을 얻음
				let commonAncestor = range.commonAncestorContainer;
				// 공통 조상이 텍스트 노드인 경우, 해당 노드의 부모로 이동
				if (commonAncestor.nodeType === 3) {
					commonAncestor = commonAncestor.parentNode;
				}

				// 모든 블록 요소를 담고 있는 배열
				const blocks = contentEl.querySelectorAll('p, h1, h2, h3, li, img'); // 예시로 'p' 태그를 사용했습니다.
				// 선택된 텍스트를 포함하는 블록의 인덱스를 찾음
				for (let i = 0; i < blocks.length; i++) {
					if (blocks[i] === commonAncestor || blocks[i].contains(commonAncestor)) {
						console.log('Block Index:', i); // 선택된 블록의 인덱스를 출력
						break;
					}
				}
			}
		}
	}

	function calculateRelativeOffsets() {
		findBlockIndex();
		const selection = window.getSelection();
		if (selection.rangeCount > 0) {
			const range = selection.getRangeAt(0);
			const selectedText = selection.toString();

			if (selectedText.length > 0) {
				let commonAncestor = range.commonAncestorContainer;

				// 공통 조상이 텍스트 노드이면 부모 노드를 사용
				if (commonAncestor.nodeType === 3) {
					commonAncestor = commonAncestor.parentNode;
				}

				// 선택된 범위의 전체 텍스트를 포함하는 컨테이너 내에서의 시작과 끝 오프셋 계산
				const startOffset =
					getGlobalOffset(commonAncestor, range.startContainer) + range.startOffset;
				const endOffset = getGlobalOffset(commonAncestor, range.endContainer) + range.endOffset;

				console.log('Global Start Offset:', startOffset);
				console.log('Global End Offset:', endOffset);
			}
		}
	}

	function getGlobalOffset(container, node) {
		let offset = 0;
		let child = container.firstChild;

		// 컨테이너의 첫 번째 자식부터 시작하여 노드를 찾을 때까지 텍스트의 길이를 더함
		while (child && child !== node) {
			if (child.nodeType === 3 || child.nodeType === 1) {
				// 텍스트 노드 또는 요소 노드
				offset += child.textContent.length;
			}
			child = child.nextSibling;
		}
		return offset;
	}
</script>

<p>안뇽???</p>

<div role="button" tabindex="0" bind:this={contentEl} on:mouseup={calculateRelativeOffsets}>
	{@html content}
</div>

<style>
	::selection {
		background-color: yellow;
		color: black;
	}
</style>
