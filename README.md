Express 프레임워크를 사용하여 작성된 Node.js 기반 백엔드 서버.

Sequelize를 ORM으로 사용하였음.

1. 사용자 API

(POST) `/users` 닉네임, 비밀번호, 비밀번호 확인 제공받아 닉네임이 중복되는 사용자가 있는지 확인한다. 조건에 부합한다면 새로운 사용자를 생성한다.

(POST) `/login` 닉네임, 비밀번호 제공받아 로그인. JWT 토큰을 생성하고 쿠키 설정.

(POST) `/logout` 인증 쿠키를 제거하여 로그아웃 처리.

2. 게시글 API

(POST) `/posts` 제목, 내용 제공받아 새로운 게시글 생성. 사용자는 authMiddleware를 통해 인증되어야 함.

(GET) `/posts` 좋아요 갯수, 생성 날짜를 기준으로 게시글 목록을 가져옴.

(GET) `/posts/:postId` postId로 특정 게시글을 가져옴.

(PUT) `/posts/:postId` postId 게시글의 제목, 내용 제공받아 수정. 사용자는 authMiddleware를 통해 인증되어야 하고, 권한이 존재해야 함.

(DELETE) `/posts/:postId` postId 게시글 삭제. 사용자는 authMiddleware를 통해 인증되어야 하고, 권한이 존재해야 함.

3. 좋아요 API

(POST) `/likes/:postId` 게시글에 좋아요, 이미 좋아요를 누른 경우 좋아요 취소. 사용자는 authMiddleware를 통해 인증되어야 함.

4. 댓글 API

(POST) `/comments/:postId` 특정 게시글에 새로운 댓글을 추가. 사용자는 authMiddleware를 통해 인증되어야 함.

(GET) `/comments/:postId` 특정 게시글에 대한 모든 댓글을 가져옴.

(PUT) `/comments/:postId/:commentId` 댓글의 내용을 수정. 사용자는 authMiddleware를 통해 인증되어야 하고, 권한이 존재해야 함.

(DELETE) `/comments/:postId/:commentId` 댓글을 삭제. 사용자는 authMiddleware를 통해 인증되어야 하고, 권한이 존재해야 함.
