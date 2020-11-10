ibatis의 다이나믹  쿼리
	- 파라미터으로 전달받은 값에 따라서 쿼리를 동적으로 생성하는 것
	- 형식
		select column, column, ...
		from table
		<dynamic>
			동적 SQL 요소를 정의한다.
		</dynamic>
	- 동적 SQL 태그
		* 이항연산 태그
		<isEqual 	property="필드명" compareValue="값"></isEqual>
		<isNotEqual 	property="" compareValue=""></isNotEqual>
		<isGreaterThan 	property="" compareValue=""></isGreaterThan>
		<isGreaterEqual property="" compareValue=""></isGreaterEqual>
		<isLessThan 	property="" compareValue=""></isLessThan>
		<isLessEqual 	property="" compareValue=""></isLessEqual>
		* property : 전달받은 값을 담고 있는 필드명
		* compareValue : 필드에 들어있는 값과 비교할 값
		
		* 단항연산 태그
		<isNull		property="필드명"></isNull>
		<isNotNull	property="필드명"></isNotNull>
		<isEmpty	property="필드명"></isEmpty>	빈문자열, 크기가 0인 콜렉션
		<isNotEmpty	property="필드명"></isNotEmpty>
		활용예)
		<select id="searchProducts" parameterClass="map" resultClass="Product"> 
			select *
			from tb_products
			<dynamic>
				<isEqual property="opt" compareValue="NAME">
					where prod_name = #keyword#
				</isEqual>
				<isEqual property="opt" compareValue="MAKER">
					where prod_maker = #keyword#
				</isEqual>
				<isEqual property="opt" compareValue="PRICE">
					where prod_price >= #keyword#
				</isEqual>
			</dynamic>
		</select> 
			
		
