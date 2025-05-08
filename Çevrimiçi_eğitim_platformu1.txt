--
-- PostgreSQL database dump
--

-- Dumped from database version 17.4
-- Dumped by pg_dump version 17.4

-- Started on 2025-05-08 12:43:31 +03

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET transaction_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- TOC entry 229 (class 1259 OID 17273)
-- Name: blog_posts; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.blog_posts (
    id integer NOT NULL,
    title character varying(255) NOT NULL,
    content text NOT NULL,
    published_at timestamp without time zone DEFAULT now(),
    member_id integer NOT NULL
);


ALTER TABLE public.blog_posts OWNER TO postgres;

--
-- TOC entry 228 (class 1259 OID 17272)
-- Name: blog_posts_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.blog_posts_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER SEQUENCE public.blog_posts_id_seq OWNER TO postgres;

--
-- TOC entry 3675 (class 0 OID 0)
-- Dependencies: 228
-- Name: blog_posts_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.blog_posts_id_seq OWNED BY public.blog_posts.id;


--
-- TOC entry 217 (class 1259 OID 17175)
-- Name: categories; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.categories (
    id smallint NOT NULL,
    name character varying(100) NOT NULL
);


ALTER TABLE public.categories OWNER TO postgres;

--
-- TOC entry 225 (class 1259 OID 17224)
-- Name: certificate_assignments; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.certificate_assignments (
    id integer NOT NULL,
    member_id integer NOT NULL,
    certificate_id integer NOT NULL,
    received_date date
);


ALTER TABLE public.certificate_assignments OWNER TO postgres;

--
-- TOC entry 224 (class 1259 OID 17223)
-- Name: certificate_assignments_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.certificate_assignments_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER SEQUENCE public.certificate_assignments_id_seq OWNER TO postgres;

--
-- TOC entry 3676 (class 0 OID 0)
-- Dependencies: 224
-- Name: certificate_assignments_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.certificate_assignments_id_seq OWNED BY public.certificate_assignments.id;


--
-- TOC entry 223 (class 1259 OID 17215)
-- Name: certificates; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.certificates (
    id integer NOT NULL,
    code character varying(100) NOT NULL,
    issued_date date
);


ALTER TABLE public.certificates OWNER TO postgres;

--
-- TOC entry 222 (class 1259 OID 17214)
-- Name: certificates_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.certificates_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER SEQUENCE public.certificates_id_seq OWNER TO postgres;

--
-- TOC entry 3677 (class 0 OID 0)
-- Dependencies: 222
-- Name: certificates_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.certificates_id_seq OWNED BY public.certificates.id;


--
-- TOC entry 219 (class 1259 OID 17183)
-- Name: courses; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.courses (
    id integer NOT NULL,
    ad character varying(200) NOT NULL,
    aciklama text,
    baslama_tarihi date,
    bitis_tarihi date,
    egitmen_bilgisi character varying(100),
    category_id smallint
);


ALTER TABLE public.courses OWNER TO postgres;

--
-- TOC entry 218 (class 1259 OID 17182)
-- Name: courses_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.courses_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER SEQUENCE public.courses_id_seq OWNER TO postgres;

--
-- TOC entry 3678 (class 0 OID 0)
-- Dependencies: 218
-- Name: courses_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.courses_id_seq OWNED BY public.courses.id;


--
-- TOC entry 221 (class 1259 OID 17197)
-- Name: enrollments; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.enrollments (
    id integer NOT NULL,
    member_id integer NOT NULL,
    course_id integer NOT NULL,
    enrolled_at timestamp without time zone DEFAULT CURRENT_TIMESTAMP
);


ALTER TABLE public.enrollments OWNER TO postgres;

--
-- TOC entry 220 (class 1259 OID 17196)
-- Name: enrollments_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.enrollments_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER SEQUENCE public.enrollments_id_seq OWNER TO postgres;

--
-- TOC entry 3679 (class 0 OID 0)
-- Dependencies: 220
-- Name: enrollments_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.enrollments_id_seq OWNED BY public.enrollments.id;


--
-- TOC entry 227 (class 1259 OID 17258)
-- Name: members; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.members (
    id integer NOT NULL,
    username character varying(50) NOT NULL,
    email character varying(100) NOT NULL,
    password character varying(255) NOT NULL,
    registration_date timestamp without time zone DEFAULT CURRENT_TIMESTAMP,
    first_name character varying(50) NOT NULL,
    last_name character varying(50) NOT NULL
);


ALTER TABLE public.members OWNER TO postgres;

--
-- TOC entry 226 (class 1259 OID 17257)
-- Name: members_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.members_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER SEQUENCE public.members_id_seq OWNER TO postgres;

--
-- TOC entry 3680 (class 0 OID 0)
-- Dependencies: 226
-- Name: members_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.members_id_seq OWNED BY public.members.id;


--
-- TOC entry 3479 (class 2604 OID 17276)
-- Name: blog_posts id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.blog_posts ALTER COLUMN id SET DEFAULT nextval('public.blog_posts_id_seq'::regclass);


--
-- TOC entry 3476 (class 2604 OID 17227)
-- Name: certificate_assignments id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificate_assignments ALTER COLUMN id SET DEFAULT nextval('public.certificate_assignments_id_seq'::regclass);


--
-- TOC entry 3475 (class 2604 OID 17218)
-- Name: certificates id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificates ALTER COLUMN id SET DEFAULT nextval('public.certificates_id_seq'::regclass);


--
-- TOC entry 3472 (class 2604 OID 17186)
-- Name: courses id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.courses ALTER COLUMN id SET DEFAULT nextval('public.courses_id_seq'::regclass);


--
-- TOC entry 3473 (class 2604 OID 17200)
-- Name: enrollments id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.enrollments ALTER COLUMN id SET DEFAULT nextval('public.enrollments_id_seq'::regclass);


--
-- TOC entry 3477 (class 2604 OID 17261)
-- Name: members id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.members ALTER COLUMN id SET DEFAULT nextval('public.members_id_seq'::regclass);


--
-- TOC entry 3669 (class 0 OID 17273)
-- Dependencies: 229
-- Data for Name: blog_posts; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.blog_posts (id, title, content, published_at, member_id) FROM stdin;
\.


--
-- TOC entry 3657 (class 0 OID 17175)
-- Dependencies: 217
-- Data for Name: categories; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.categories (id, name) FROM stdin;
\.


--
-- TOC entry 3665 (class 0 OID 17224)
-- Dependencies: 225
-- Data for Name: certificate_assignments; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.certificate_assignments (id, member_id, certificate_id, received_date) FROM stdin;
\.


--
-- TOC entry 3663 (class 0 OID 17215)
-- Dependencies: 223
-- Data for Name: certificates; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.certificates (id, code, issued_date) FROM stdin;
\.


--
-- TOC entry 3659 (class 0 OID 17183)
-- Dependencies: 219
-- Data for Name: courses; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.courses (id, ad, aciklama, baslama_tarihi, bitis_tarihi, egitmen_bilgisi, category_id) FROM stdin;
\.


--
-- TOC entry 3661 (class 0 OID 17197)
-- Dependencies: 221
-- Data for Name: enrollments; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.enrollments (id, member_id, course_id, enrolled_at) FROM stdin;
\.


--
-- TOC entry 3667 (class 0 OID 17258)
-- Dependencies: 227
-- Data for Name: members; Type: TABLE DATA; Schema: public; Owner: postgres
--

COPY public.members (id, username, email, password, registration_date, first_name, last_name) FROM stdin;
\.


--
-- TOC entry 3681 (class 0 OID 0)
-- Dependencies: 228
-- Name: blog_posts_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.blog_posts_id_seq', 1, false);


--
-- TOC entry 3682 (class 0 OID 0)
-- Dependencies: 224
-- Name: certificate_assignments_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.certificate_assignments_id_seq', 6, true);


--
-- TOC entry 3683 (class 0 OID 0)
-- Dependencies: 222
-- Name: certificates_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.certificates_id_seq', 2, true);


--
-- TOC entry 3684 (class 0 OID 0)
-- Dependencies: 218
-- Name: courses_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.courses_id_seq', 2, true);


--
-- TOC entry 3685 (class 0 OID 0)
-- Dependencies: 220
-- Name: enrollments_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.enrollments_id_seq', 6, true);


--
-- TOC entry 3686 (class 0 OID 0)
-- Dependencies: 226
-- Name: members_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.members_id_seq', 1, false);


--
-- TOC entry 3502 (class 2606 OID 17281)
-- Name: blog_posts blog_posts_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.blog_posts
    ADD CONSTRAINT blog_posts_pkey PRIMARY KEY (id);


--
-- TOC entry 3482 (class 2606 OID 17181)
-- Name: categories categories_name_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.categories
    ADD CONSTRAINT categories_name_key UNIQUE (name);


--
-- TOC entry 3484 (class 2606 OID 17179)
-- Name: categories categories_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.categories
    ADD CONSTRAINT categories_pkey PRIMARY KEY (id);


--
-- TOC entry 3494 (class 2606 OID 17229)
-- Name: certificate_assignments certificate_assignments_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificate_assignments
    ADD CONSTRAINT certificate_assignments_pkey PRIMARY KEY (id);


--
-- TOC entry 3490 (class 2606 OID 17222)
-- Name: certificates certificates_code_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificates
    ADD CONSTRAINT certificates_code_key UNIQUE (code);


--
-- TOC entry 3492 (class 2606 OID 17220)
-- Name: certificates certificates_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificates
    ADD CONSTRAINT certificates_pkey PRIMARY KEY (id);


--
-- TOC entry 3486 (class 2606 OID 17190)
-- Name: courses courses_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.courses
    ADD CONSTRAINT courses_pkey PRIMARY KEY (id);


--
-- TOC entry 3488 (class 2606 OID 17203)
-- Name: enrollments enrollments_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.enrollments
    ADD CONSTRAINT enrollments_pkey PRIMARY KEY (id);


--
-- TOC entry 3496 (class 2606 OID 17270)
-- Name: members members_email_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.members
    ADD CONSTRAINT members_email_key UNIQUE (email);


--
-- TOC entry 3498 (class 2606 OID 17266)
-- Name: members members_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.members
    ADD CONSTRAINT members_pkey PRIMARY KEY (id);


--
-- TOC entry 3500 (class 2606 OID 17268)
-- Name: members members_username_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.members
    ADD CONSTRAINT members_username_key UNIQUE (username);


--
-- TOC entry 3510 (class 2606 OID 17282)
-- Name: blog_posts blog_posts_author_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.blog_posts
    ADD CONSTRAINT blog_posts_author_id_fkey FOREIGN KEY (member_id) REFERENCES public.members(id);


--
-- TOC entry 3508 (class 2606 OID 17235)
-- Name: certificate_assignments certificate_assignments_certificate_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificate_assignments
    ADD CONSTRAINT certificate_assignments_certificate_id_fkey FOREIGN KEY (certificate_id) REFERENCES public.certificates(id);


--
-- TOC entry 3503 (class 2606 OID 17191)
-- Name: courses courses_category_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.courses
    ADD CONSTRAINT courses_category_id_fkey FOREIGN KEY (category_id) REFERENCES public.categories(id);


--
-- TOC entry 3505 (class 2606 OID 17209)
-- Name: enrollments enrollments_course_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.enrollments
    ADD CONSTRAINT enrollments_course_id_fkey FOREIGN KEY (course_id) REFERENCES public.courses(id);


--
-- TOC entry 3511 (class 2606 OID 17287)
-- Name: blog_posts fk_blogposts_member; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.blog_posts
    ADD CONSTRAINT fk_blogposts_member FOREIGN KEY (member_id) REFERENCES public.members(id);


--
-- TOC entry 3509 (class 2606 OID 17292)
-- Name: certificate_assignments fk_certificateassignments_member; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.certificate_assignments
    ADD CONSTRAINT fk_certificateassignments_member FOREIGN KEY (member_id) REFERENCES public.members(id);


--
-- TOC entry 3504 (class 2606 OID 17297)
-- Name: courses fk_courses_category; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.courses
    ADD CONSTRAINT fk_courses_category FOREIGN KEY (category_id) REFERENCES public.categories(id);


--
-- TOC entry 3506 (class 2606 OID 17307)
-- Name: enrollments fk_enrollments_course; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.enrollments
    ADD CONSTRAINT fk_enrollments_course FOREIGN KEY (course_id) REFERENCES public.courses(id);


--
-- TOC entry 3507 (class 2606 OID 17302)
-- Name: enrollments fk_enrollments_member; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.enrollments
    ADD CONSTRAINT fk_enrollments_member FOREIGN KEY (member_id) REFERENCES public.members(id);


-- Completed on 2025-05-08 12:43:31 +03

--
-- PostgreSQL database dump complete
--

