# Front-BackProject

> 프로젝트 주제

영화 리뷰(소개) 사이트로 컨셉.

프론트단과 백단을 연결시킨 첫번째 프로젝트.

***

> 사용기술
  * java
  * jsp
  * mysql

> 주요기능
  - 회원가입 기능
  - 로그인 기능
  - 글 CRUD 기능
  - 글 검색 기능
  - 파일 업로드 기능

***

> BoardDAO중의 일부

```java

public List<Board> selectList() throws Exception {
		Connection connection = null;
		Statement stmt = null;
		ResultSet rs = null;
		final String sqlSelect = "SELECT post_id,title,post_content from post ORDER BY post_id ASC";

		try {
			// 커넥션 풀에서 Connection객체를 빌려온다
			connection = ds.getConnection();

			stmt = connection.createStatement();
			rs = stmt.executeQuery(sqlSelect);

			ArrayList<Board> selectAllBoard = new ArrayList<Board>();

			while (rs.next()) {
				selectAllBoard.add(new Board().setNo(rs.getInt("post_id")).setTitle(rs.getString("title"))
						.setContent(rs.getString("post_content")));
			}

			return selectAllBoard;

		} catch (Exception e) {
			throw e;
		} finally {
			try {
				if (rs != null)
					rs.close();
			} catch (Exception e) {
				e.printStackTrace();
			}
			try {
				if (stmt != null)
					stmt.close();
			} catch (Exception e) {
				e.printStackTrace();
			}

			try {
				if (connection != null)
					connection.close();
			} catch (Exception e) {
				e.printStackTrace();
			}
		}
	}
  
  ```
  
