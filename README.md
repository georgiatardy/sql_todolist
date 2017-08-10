Created a database called todolist, write a set of SQL statements in a file called sql_todo_list.sql.

Write INSERT statements to insert 20 todos into the todos table, with a combination of priorities, created times, and completed times, with not all having a completed time.
Write a SELECT statement to find all incomplete todos with priority 3.
Write a SELECT statement to find the number of incomplete todos by priority.
Write a SELECT statement to find the number of todos by priority created in the last 30 days.
Write a SELECT statement to find the next todo you should work on. This is the todo with the highest priority that was created first.


==============================================================================================================


--
-- PostgreSQL database dump
--

-- Dumped from database version 9.6.3
-- Dumped by pg_dump version 9.6.3

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SET check_function_bodies = false;
SET client_min_messages = warning;
SET row_security = off;

--
-- Name: plpgsql; Type: EXTENSION; Schema: -; Owner:
--

CREATE EXTENSION IF NOT EXISTS plpgsql WITH SCHEMA pg_catalog;


--
-- Name: EXTENSION plpgsql; Type: COMMENT; Schema: -; Owner:
--

COMMENT ON EXTENSION plpgsql IS 'PL/pgSQL procedural language';


SET search_path = public, pg_catalog;

SET default_tablespace = '';

SET default_with_oids = false;

--
-- Name: todos; Type: TABLE; Schema: public; Owner: reggieandgeorgiatardy
--

CREATE TABLE todos (
    id integer NOT NULL,
    title character varying(255) NOT NULL,
    details character varying(3000),
    priority integer DEFAULT 1 NOT NULL,
    created_at timestamp without time zone NOT NULL,
    completed_at timestamp without time zone
);


ALTER TABLE todos OWNER TO reggieandgeorgiatardy;

--
-- Name: todos_id_seq; Type: SEQUENCE; Schema: public; Owner: reggieandgeorgiatardy
--

CREATE SEQUENCE todos_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE todos_id_seq OWNER TO reggieandgeorgiatardy;

--
-- Name: todos_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: reggieandgeorgiatardy
--

ALTER SEQUENCE todos_id_seq OWNED BY todos.id;


--
-- Name: todos id; Type: DEFAULT; Schema: public; Owner: reggieandgeorgiatardy
--

ALTER TABLE ONLY todos ALTER COLUMN id SET DEFAULT nextval('todos_id_seq'::regclass);


--
-- Data for Name: todos; Type: TABLE DATA; Schema: public; Owner: reggieandgeorgiatardy
--

COPY todos (id, title, details, priority, created_at, completed_at) FROM stdin;
1	garbage	take out trash	2	2017-08-10 13:50:57.559513	\N
2	dishes	load dishwasher	2	2017-08-10 13:56:13.662145	\N
4	car	vacuum	4	2017-08-10 13:59:48.989198	\N
5	car	wash exterior	4	2017-08-10 13:59:48.989198	\N
6	car	oil change	1	2017-08-10 14:04:35.803565	\N
7	car	rotate tires	1	2017-08-10 14:04:35.803565	\N
8	laundry	wash clothes	1	2017-08-10 14:04:35.803565	\N
9	laundry	fold clothes	3	2017-08-10 14:07:33.323603	\N
10	laundry	put clothes away	3	2017-08-10 14:07:33.323603	\N
11	carpet	shampoo carpet	2	2017-08-10 14:07:33.323603	\N
12	donate clothes	gather old clothes	5	2017-08-10 14:13:05.340761	\N
13	donate clothes	throw clothes away	5	2017-08-10 14:13:05.340761	\N
14	donate clothes	take to Goodwill	5	2017-08-10 14:13:05.340761	\N
15	bank	make deposit	1	2017-08-10 14:17:11.615535	\N
16	bank	apply for loan	2	2017-08-10 14:17:11.615535	\N
17	shopping	grocery shopping	2	2017-08-10 14:17:11.615535	\N
18	shopping	buy shoes	3	2017-08-10 14:22:14.753235	\N
19	shopping	buy jeans	3	2017-08-10 14:22:14.753235	\N
20	shopping	but shirts	2	2017-08-10 14:22:14.753235	\N
21	yard	rake leaves	3	2017-08-10 14:22:14.753235	\N
22	yard	bag leaves	3	2017-08-10 14:22:14.753235	\N
23	yard	mow front lawn	1	2017-08-10 14:24:47.482343	\N
24	paint	bathroom walls	5	2017-08-10 14:24:47.482343	\N
25	paint	bedroom walls	1	2017-08-10 14:24:47.482343	\N
3	dishes	unload dishwasher	3	2017-08-10 13:59:48.989198	2017-08-10 14:32:54.398923
\.


--
-- Name: todos_id_seq; Type: SEQUENCE SET; Schema: public; Owner: reggieandgeorgiatardy
--

SELECT pg_catalog.setval('todos_id_seq', 25, true);


--
-- Name: todos todos_pkey; Type: CONSTRAINT; Schema: public; Owner: reggieandgeorgiatardy
--

ALTER TABLE ONLY todos
    ADD CONSTRAINT todos_pkey PRIMARY KEY (id);


--
-- PostgreSQL database dump complete
--
